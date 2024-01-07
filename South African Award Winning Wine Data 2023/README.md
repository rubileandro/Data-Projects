# How much does award-winning wine cost in South Africa in 2024?

## Original Source 
The original source for the data is the online publisher Top Wine SA. The are well-established experts and collect data from various expert sources within the South African Wine market and keep track of the best wines based on local as well as international judges.
This data was published in 2023.

Top Wine SA – Top SA Wine Ratings
https://topwinesa.com/top-sa-wines-and-cellars/top-sa-wine-ratings/

Here is a mirror of the data:
https://web.archive.org/web/20240107032540/https://topwinesa.com/top-sa-wines-and-cellars/top-sa-wine-ratings/

## A Note on Categories
The original dataset provides the following description regarding categories:

“Prices are given in South African rand (R) per standard bottle size (750ml), unless stated otherwise, and are inclusive of VAT – prices as supplied by the producers, or approximate retail prices in South Africa if the producers are closed to the public – top wines may well be ‘sold out’ or increase in price after a stellar rating.

Note: AW = Auction Wine, EXP = Export Only, MC = Museum Class (typically ‘sold out’ at the winery, assessed to gauge development or longevity), and OL = Own Label (exclusive to particular retailer(s), not available from the producer).”

I removed these categories because my focus is on what the average South African consumer is paying for. 

Wine that is export only is automatically excluded from this this case. As is Museum Class and Auction Wine. Although some Own Label wines were not too difficult to find, I was not able to find all of them so for this reason I have excluded these.

Below I have listed how many in each of these particular categories there were, before removing them.

    • AW: 8
    • EX: 21
    • MC: 4
    • OL: 16

## A Note on Awards
This report is not implying that only wines that have won awards are ‘good’ wines. For the purposes of this report in particular, I am only looking at award-winning wines. 
Some of the best wines I have had did not have an award at the time I bought them, but only a year or two later did the same wine and vintage win an award.
There are wines in South Africa that are still exceptionally good, but for a variety of reasons, do not have awards.

## The Process 
I manually copied the data from the TOP SA wines website at this address:
https://topwinesa.com/top-sa-wines-and-cellars/top-sa-wine-ratings/

I added in an extra column for Category and Second Category. And assigned the relevant category to each one.

I cleaned up the data which involved sorting and deleting unnecessary rows. There were blank cells in some columns as some wines had more than one award. I removed the any additional awards as the focus of this data set is that there are the wines, vintages, and prices that consumers are paying for, for award-winning South Africa wine (as opposed to the particular award that won). 

Then I deleted all entries of the categories mentioned above (AW, EX, MC, OL).

The prices were entered as text with the letter “R”. I used a formula in excel to remove the letter “R” from the price column so that the price could be stored as a number.

`=IF(ISNUMBER(VALUE(SUBSTITUTE(B2,"R ",""))), VALUE(SUBSTITUTE(B2,"R ","")), "")`

I wanted to have the vintage as its own column. So I used a formula to extract the numbers from the wine names provided. For most of the entries, the year was the only number in the name. For those entries that had additional numbers in the name, I manually fixed those cases.

`=IFERROR(VALUE(TEXTJOIN("", TRUE, IF(ISNUMBER(--MID(A2, ROW(INDIRECT("1:" & LEN(A2))), 1)), MID(A2, ROW(INDIRECT("1:" & LEN(A2))), 1), ""))), "")`


## Key Findings

### Price Distribution Curve
From the data it shows that 80% of award winning red wines (red blends and red single varietals) are R500 and less.

|  			Red Blends and Red Single Varietals		 |  		 		 |
|--------------------------------|-------|
|  			Percentage 			of R500 and under 		 |  			80% 		 |
|  			Percentage 			of R400 and under 		 |  			68% 		 |
|  			Percentage 			of R300 and under 		 |  			55% 		 |
|  			Percentage 			of R200 and under 		 |  			27% 		 |

![Frequency Distribution of Red and Red Blend Wine Prices](https://github.com/rubileandro/Data-Projects/assets/93342175/b0f2272a-ae46-4573-9d96-8428a4b37507)

### Violin Plot Chart 
Here is a chart comparing the price distribution between Shiraz / Syrah and Pinotage. We can see that the Shiraz / Syrah price is very concentrated around the R250 price point, whereas the price for Pinotage is more distributed. Pinotage is also more likely to have very expensive wines.

![Price Distribution comparing Shiraz and Pinotage](https://github.com/rubileandro/Data-Projects/assets/93342175/d5077288-0059-458c-8c69-9d2d4d77ab72)

### Heatmap of Average Wine Prices by Category and Vintage
The majority of the most expensive wines fell within the narrow band of years between 2017-2019. 

![Heatmap of Average Wine Prices by Category and Vintage](https://github.com/rubileandro/Data-Projects/assets/93342175/c7fe3901-0790-4e88-8864-b234cbfabcfe)

## Consumer take-away
In general, in South Africa it is quite easy to get an award-winning wine at a very affordable price. 
For your average wine drinker, they don’t need to spend in excess of R500 for a very good, award-winning bottle of wine.

## Special Thanks
Thank you to Top Wine SA for their extensive work in the field, and making their data freely available.
