# Making Things With Sticks and String

## An Exploration of Data About Yarn Artists and What They Like

## Table of Contents
* [Motivation](#motivation)
* [Data](#data)
* [Analytical Approach](#analytical-approach)
* [Tools Used](#tools-used)
* [Sources](#sources)

### Motivation
My personal motivation for choosing this project was simple - I really like knitting! I see yarn crafting as a way to connect sometimes disparate parts of my life together. When I'm working on a project, it brings together memories of where I was when I bought the yarn and the friends I was with or the class I took on a particular technique. Projects like the cardigan I made for my dad several years ago represent my ability to overcome challenges, and making items for my nieces and nephew are a way to show how much I care by spending time making things for them to enjoy.

While not everyone will take up knitting or crochet, I do think this topic is interesting to a wider audience for several reasons:
1. Millions of people of all ages in the US knit and/or crochet. It can be a great way for adults to meet new people.
2. Yarn crafts are big business, and locally-owned independent shops account for a large portion of that. Yarn crafters care about supporting local businesses.
3. Repetitive non-verbal tasks can help people pay better attention in meetings or lectures by occupying the part of the brain that wants to move, and that would otherwise distract from focused attention. In other words, knitting and crochet are basically a productive way to fidget!
Lastly, the practice of knitting or crochet can have several health benefits, including decreased blood pressure through the "relaxation response" similar to yoga, relief from chronic pain, and improved cognition.

I was interested in looking at available data to answer several related questions:
1. Where are local yarn shops currently located in the US?
2. What areas of the US would be able to support additional shops?
3. What are characteristics of popular patterns?
4. What are characteristics of popular yarns?

### Data
To answer these questions, I used data obtained from Ravelry through their API. I also used population data from the US Census Bureau to determine potential areas of interest for new yarn shops, and a county-level shape file also from the US Census Bureau for mapping.

### Analytical Approach
Using the Ravelry API, I retrieved data in three areas: patterns, yarns, and shops.

After looking at some initial test data, I chose to get full details for the top 30,000 patterns in the database ordered by project count. This cut the tail off at approximately 100 projects associated with the least popular pattern which I judged to be a sufficient number to show that the pattern appealed to more than a small group of people. There were 11 million user-created projects associated with this set of patterns.

I followed the same procedure to get data on yarns. I cut the tail off on this data at approximately 200 patterns, judging that a sufficient number to ensure the yarn was a commercially viable product. That gave me 10,000 yarns in the dataset.

For the shop information, I got information from all shops located in the US (not including territories). Once duplicates and records with null values for location were dropped, there were approximately 2100 shop records in the dataset.

County-level population estimates were downloaded from the US Census Bureau as a csv file, and the shapefile was from the same source.

Challenges encountered while working through this project were primarily with using the API to get the relevant data.  I was not previously familiar with API methods or with web coding in general. This was a greater challenge than I had anticipated, and I spent a lot of time on this part of the project. The second major challenge was cleaning the data, particularly the nested "dictionary" columns.

Once the data was cleaned, I used the shop and population data to determine what population level was necessary to support a local shop. This calculation was made by taking the county population and dividing it by the number of shops located in that county. This gave a wide range from around 500 to 2.25 million. I chose the median (56,000) and used that to calculate goo locations for potential new yarn shops. I also mapped the highest concentrations on current shops as a point of interest for crafters visiting those cities.

I analyzed the pattern and yarn data to determine what categories of patterns and yarn are most popular to find some common characteristics.

### Tools Used
- 'Python/Pandas' - for getting and cleaning data, exploration, analysis and creating visuals
- 'Atom' - for editing html/markdown files
- 'Terminal/GitHub' - for version control

### Sources
Pattern, yarn, and local shop data was retrieved from:

<a href = "https://www.ravelry.com/"> Ravelry</a>

US Census Bureau Population Estimates for 2019:

<a href = "https://www.census.gov/data/datasets/time-series/demo/popest/2010s-counties-total.html"> County Population Totals: 2010-2019</a>

Further information from:

<a href = "https://www.craftandhobby.org/eWeb/pdfs/AFCI%20MASTER%20Report_020117.pdf"> 2016 Creative Products Size of the Industry Study</a>

<a href = "https://www.medscape.com/viewarticle/916712"> The Knitting Lady is Paying Attention</a>

<a href = "https://www.medicalbag.com/home/lifestyle/knit-one-purl-one-the-health-benefits-of-knitting/"> Knit One, Purl One: The Health Benefits of Knitting</a>

<a href = "https://tnna.org/?page=Research"> TNNA reports "The State of Specialty NeedleArts 2013" and" Knitter Survey Results 2013" (not currently available online as of June 2020)</a>
