# Feeding_America
Group Project for Intro to Digital Humanities Course, Vrije Universiteit Amsterdam

Data Provenance

Our data is derived from 76 influential American cookbooks held by Michigan State University Library’s Stephen O. Murray and Keelung Hong Special Collections. It was created to be representative of periods and themes in American cookbook history spanning the late 18th- to early 20th-centuries. Collected in an attempt to highlight “an important part of America’s cultural heritage,” the dataset was specifically intended for use by teachers, students, and researchers investigating the subject, as well as chefs.
The "Feeding America: The Historic American Cookbook" dataset contains 76 plaintext files of transcribed cookbooks, 76 XML files of encoded cookbook text, 1 XML file that includes metadata records for each cookbook in the dataset, and 1 DTD file that describes the schema used to encode the cookbooks. The 76 cookbooks used in the dataset were chosen among a larger collection of more than 7000. This subselection’s level of representation for the whole is unclear, as the requirements for inclusion were not clearly defined. As such, the data could have been selected with some amount of bias. 
The publisher has stated that they enhanced the data by adding some of the texts’ features, including recipe, recipe type, ingredient, measurements and cooking implements. In the original dataset, columns for only book_id, year, ethnicgroup, recipe class, region and ingredients are included. In supplemental files we have found the list of cookbook titles and their contents in text format, though we have yet to find the referenced measurements and cooking implements in any of these files. 
Physical aspects that may have been lost in digitalization include images of the book covers, the physical state of the books, and the type of binding and materials used. .The dataset is publicly available for anyone to download, additionally the site does not mention anything about licensing. Furthermore data.4tu mentions that publicly published data can freely be used in research as long as credit is given through citation: 
https://data.4tu.nl/info/en/use/publish-cite/upload-your-data-in-our-data-repository/licencing)


Quality

The columns in the primary dataset include book_id (short names in .xml format), date (year only, presumably of publication), ethnicgroup, recipe_class, region, and ingredients. The entries in the ingredients column include each ingredient delimited with semicolons.
The dataset includes 48,032 rows in total. Every column is complete except the ethnic group column, with 41,431 rows missing data. We do not fully comprehend the structure of the metadata and cannot determine if this is complete. Though it is in a spreadsheet-like format, it seems to have almost been intended for a more plaintext type presentation, and fields seem to be inconsistently filled in, perhaps dependent on the inconsistent formatting of the actual publishing page from book to book.
Finally, the quality of the digitization is very high. The text has not been processed through OCR but rather was transcribed. 


Data Preparation

Seeing as our dataset had numerous limitations with regards to its provenance and thoroughness, our analysis had to be limited to what data remained. The main columns we initially had to work with included a coded name for each of the 74 book codes (a pair of which actually represent one book, split in two), the date of publication, a tag for ethnic group (which was often left blank), a tag for recipe class, and a delimited list of ingredients in one string. 

The first step after initial exploratory analysis was to separate each of the ingredients into their own columns. The least amount of ingredients contained in any one recipe was 1, the most was 57, and the total number of discretely-labeled ingredients was 3532. Seeing as our primary research question relied on having a score for each recipe’s content of unhealthy ingredients, we used Python to go through each recipe and compute a simple arithmetic score for how many instances of the words from our unhealthy ingredients list were present, as well as an array of how many instances of each of the unhealthy ingredients occurred. The rest of our observations about the data revolved around visualizations and simple statistical analyses of these results. 

Once we had exported our Python data back to csv format for use in Excel, the next step was cleaning the ethnic groups list to compare the ingredient scores across multiple groups. The ethnic list contained values that represented different scopes (e.g cities and countries), multiple entries, mistakes in spelling, and alternating formats e.g. “german” and “germany.” We unified these ethnic groups by separating multiple entries and adding them individually, choosing the scope of countries and cultural groups (e.g. adding cities to the right country based on research); and by fixing mistakes in spelling and choosing one universal format. Every change was recorded and can be found in the appendix in the changes to data document. 

After the cleaning of the ethnic group list, 55 groups remained, some of which only having a few (or even just one) recipe(s), so we removed all categories with less than 10 recipes (in total, 30 groups) from our analysis to improve the significance of our conclusion. 
The outliers in the average amount of unhealthy ingredients used are years with small sample sizes, and as such, we removed years that had less than 90 recipes. 
