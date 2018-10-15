
# Capstone Project - The Battle of the Neighborhoods

## Introduction

Using the example of Toronto, other parts of Canada think Torontonians feel they are prosperous and glamorous like an American city. With a population of over 2.73 million people, is Toronto more American or Canadian. To examine this, a comparison will be done using a Canadian and an American city. The selection of these cities is explained in the Data section below. The cities select are Edmonton, pop. 930,000+, and Atlanta, pop. 480,000 – 4,975,000. Will similarities in latitude, longitude, climate or topography contribute to any similarities between Toronto and the other two cities? 

## Data

Research was done to locate cities within North America that have an open data portal to acquire data. Next, neighborhood, district, postal code, or zip code was required to open up the areas to fully catalogue each city for the use of the Foursquare API. Finally, centroid data for each geospatial division was required. This requirement is not necessary to run this comparison, but as I was unable to use the geolocator package suggested in week 3, it was necessary to obtain latitude and longitude measurements by other means. Therefore, the data acquired contains each city's location ID (zip code, postal code, or neighborhood), respective geospatial information for said location ID (latitude and longitude), and in the case of Toronto and Atlanta city name. This is a remnant from the data source.

The collection of venue data uses the Foursquare API to locate venues within the determined are based on the various identified zip codes, postal codes, or neighbourhoods within each respective city. This information will then be grouped using the groupby attribute to group by the respective divisions. Then one hot coding and grouping will be done to allow for k-means clustering of the data. This clustering will be compared in regards to number of clusters, size of clusters, and any other properties that may stand out. 

Another comparison will be the comparison of the venue locations. Is there a specific pattern? Are there large sections and small sections? Is it based on geography, topography, settlements, or highway systems? This comparison is more on the interpretation side of the project.

All data acquired for this project was obtained using open data portals for cities and the Foursquare API.

## Methodology

This project stems of segmenting and clustering neighborhood data uses the same concepts from the previous lab and assignment. Using the Toronto results from the assignment, an analytical comparison is done using the same techniques. Neighborhood and zip code data was obtain from the file to allow for exploration of their respective areas. The explore function for the Foursquare API was used on zip codes in Atlanta and neighborhoods in Edmonton. The radius selected was comparable to the one used for Toronto (500). This was to maintain as many variables as possible for proper comparison.

The explore function identifies the common venues and their respective categories, which was then used to group the neighborhoods into clusters. Due to the scarcity of data or the lack of venues in the respective zip code or neighborhood, longitudinal and latitudinal restrictions were implemented to ensure every neighborhood contained at least 1 results. This is due to the fact that when using the groupby attribute in Python any zero value will not be included in the results thereby changing the shape of the dataframe and thus not being able to continue.

Visual examination of the datasets was completed to identify which neighborhoods did not include an API result. Once determined which neighborhoods these were the longitudinal and latitudinal restrictions were created using a realistic pattern. For Atlanta a rectangle was chosen with the longer length being vertical and in the case of Edmonton a somewhat square area was chosen centered around downtown Edmonton. From this one hot coding was implemented to group together venues in each neighborhood and bin them into their respective categories then a determination of their top 10 most common venues. 

All of this was completed using k-means clustering to apply machine learning to the dataframe. The result of this was clustering of neighborhoods in each city to identify any similarities which are present in the city itself. Folium was used to visualize the emerging clusters in each city. The continued use of k-means clustering provides the inter-city comparison that is at the level that this course has taught through the lab and assignment.

# Results

## Toronto

With Toronto the postal codes are dense in the city centre and become less dense moving away from the centre of Toronto. The image below shows all assigned M postal codes in the area. This includes Toronto, York, and Etobicoke for example.

![Alt Text](https://github.com/wacky-bird/coursera_capstone_project/blob/Images/TO-start.png "Neighborhoods with M postal code")

Unassigned postal codes were eliminated from the data frame with remaining neighbourhoods being grouped together by postal codes. From this only postal codes residing in Toronto were selected and are shown in the image below.

![Alt Text](https://github.com/wacky-bird/coursera_capstone_project/blob/Images/TO-downtown.png "Downtown Toronto Data")

## Examine the Clusters for Toronto

Using the k-means clustering method, postal codes were placed into 5 clusters with the results shown in the image below in regards to their location. 

![Alt Text](https://github.com/wacky-bird/coursera_capstone_project/blob/Images/TO-cluster.png "Cluster of Toronto Data")

Cluster 1


```python
Toronto_merged.loc[Toronto_merged['Cluster Labels'] == 0, Toronto_merged.columns[[1] + list(range(5, Toronto_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Borough</th>
      <th>Cluster Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>28</th>
      <td>Downtown Toronto</td>
      <td>0</td>
      <td>Coffee Shop</td>
      <td>Café</td>
      <td>Seafood Restaurant</td>
      <td>Beer Bar</td>
      <td>Restaurant</td>
      <td>Hotel</td>
      <td>Cocktail Bar</td>
      <td>Art Gallery</td>
      <td>Lounge</td>
      <td>Farmers Market</td>
    </tr>
  </tbody>
</table>
</div>



Cluster 2


```python
Toronto_merged.loc[Toronto_merged['Cluster Labels'] == 1, Toronto_merged.columns[[1] + list(range(5, Toronto_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Borough</th>
      <th>Cluster Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>East Toronto</td>
      <td>1</td>
      <td>Coffee Shop</td>
      <td>Pub</td>
      <td>Neighborhood</td>
      <td>Music Venue</td>
      <td>Yoga Studio</td>
      <td>Dessert Shop</td>
      <td>Ethiopian Restaurant</td>
      <td>Electronics Store</td>
      <td>Eastern European Restaurant</td>
      <td>Dumpling Restaurant</td>
    </tr>
    <tr>
      <th>1</th>
      <td>East Toronto</td>
      <td>1</td>
      <td>Greek Restaurant</td>
      <td>Coffee Shop</td>
      <td>Ice Cream Shop</td>
      <td>Bookstore</td>
      <td>Italian Restaurant</td>
      <td>Dessert Shop</td>
      <td>Brewery</td>
      <td>Bubble Tea Shop</td>
      <td>Café</td>
      <td>Pub</td>
    </tr>
    <tr>
      <th>2</th>
      <td>East Toronto</td>
      <td>1</td>
      <td>Sushi Restaurant</td>
      <td>Burger Joint</td>
      <td>Steakhouse</td>
      <td>Pub</td>
      <td>Ice Cream Shop</td>
      <td>Italian Restaurant</td>
      <td>Liquor Store</td>
      <td>Hotel</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Burrito Place</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Central Toronto</td>
      <td>1</td>
      <td>Park</td>
      <td>Breakfast Spot</td>
      <td>Food &amp; Drink Shop</td>
      <td>Dance Studio</td>
      <td>Hotel</td>
      <td>Sandwich Place</td>
      <td>Burger Joint</td>
      <td>Diner</td>
      <td>Ethiopian Restaurant</td>
      <td>Electronics Store</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Central Toronto</td>
      <td>1</td>
      <td>Coffee Shop</td>
      <td>Sporting Goods Shop</td>
      <td>Yoga Studio</td>
      <td>Chinese Restaurant</td>
      <td>Sandwich Place</td>
      <td>Salon / Barbershop</td>
      <td>Fast Food Restaurant</td>
      <td>Spa</td>
      <td>Diner</td>
      <td>Italian Restaurant</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Central Toronto</td>
      <td>1</td>
      <td>Pizza Place</td>
      <td>Sandwich Place</td>
      <td>Dessert Shop</td>
      <td>Sushi Restaurant</td>
      <td>Pharmacy</td>
      <td>Café</td>
      <td>Seafood Restaurant</td>
      <td>Coffee Shop</td>
      <td>Restaurant</td>
      <td>Italian Restaurant</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Central Toronto</td>
      <td>1</td>
      <td>Gym</td>
      <td>Playground</td>
      <td>Dessert Shop</td>
      <td>Falafel Restaurant</td>
      <td>Event Space</td>
      <td>Ethiopian Restaurant</td>
      <td>Electronics Store</td>
      <td>Eastern European Restaurant</td>
      <td>Dumpling Restaurant</td>
      <td>Donut Shop</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Central Toronto</td>
      <td>1</td>
      <td>Coffee Shop</td>
      <td>Pub</td>
      <td>Sushi Restaurant</td>
      <td>American Restaurant</td>
      <td>Restaurant</td>
      <td>Bagel Shop</td>
      <td>Sports Bar</td>
      <td>Athletics &amp; Sports</td>
      <td>Supermarket</td>
      <td>Fried Chicken Joint</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Downtown Toronto</td>
      <td>1</td>
      <td>Park</td>
      <td>Playground</td>
      <td>Trail</td>
      <td>Yoga Studio</td>
      <td>Dessert Shop</td>
      <td>Event Space</td>
      <td>Ethiopian Restaurant</td>
      <td>Electronics Store</td>
      <td>Eastern European Restaurant</td>
      <td>Dumpling Restaurant</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Downtown Toronto</td>
      <td>1</td>
      <td>Restaurant</td>
      <td>Coffee Shop</td>
      <td>Pharmacy</td>
      <td>Indian Restaurant</td>
      <td>Italian Restaurant</td>
      <td>Bakery</td>
      <td>Pub</td>
      <td>Café</td>
      <td>Pizza Place</td>
      <td>Chinese Restaurant</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Downtown Toronto</td>
      <td>1</td>
      <td>Coffee Shop</td>
      <td>Bakery</td>
      <td>Park</td>
      <td>Café</td>
      <td>Pub</td>
      <td>Mexican Restaurant</td>
      <td>Breakfast Spot</td>
      <td>Theater</td>
      <td>Yoga Studio</td>
      <td>Health Food Store</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Downtown Toronto</td>
      <td>1</td>
      <td>Coffee Shop</td>
      <td>Clothing Store</td>
      <td>Café</td>
      <td>Cosmetics Shop</td>
      <td>Bar</td>
      <td>Japanese Restaurant</td>
      <td>Italian Restaurant</td>
      <td>Ramen Restaurant</td>
      <td>Plaza</td>
      <td>Sandwich Place</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Downtown Toronto</td>
      <td>1</td>
      <td>Coffee Shop</td>
      <td>Cocktail Bar</td>
      <td>Beer Bar</td>
      <td>Farmers Market</td>
      <td>Steakhouse</td>
      <td>Seafood Restaurant</td>
      <td>Cheese Shop</td>
      <td>Café</td>
      <td>Bakery</td>
      <td>Restaurant</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Downtown Toronto</td>
      <td>1</td>
      <td>Coffee Shop</td>
      <td>Café</td>
      <td>American Restaurant</td>
      <td>Steakhouse</td>
      <td>Thai Restaurant</td>
      <td>Restaurant</td>
      <td>Gym</td>
      <td>Cosmetics Shop</td>
      <td>Hotel</td>
      <td>Bar</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Downtown Toronto</td>
      <td>1</td>
      <td>Coffee Shop</td>
      <td>Hotel</td>
      <td>Aquarium</td>
      <td>Pizza Place</td>
      <td>Café</td>
      <td>Brewery</td>
      <td>Italian Restaurant</td>
      <td>Sports Bar</td>
      <td>Scenic Lookout</td>
      <td>Fried Chicken Joint</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Downtown Toronto</td>
      <td>1</td>
      <td>Coffee Shop</td>
      <td>Hotel</td>
      <td>Café</td>
      <td>American Restaurant</td>
      <td>Sports Bar</td>
      <td>Gym</td>
      <td>Restaurant</td>
      <td>Italian Restaurant</td>
      <td>Deli / Bodega</td>
      <td>Gastropub</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Central Toronto</td>
      <td>1</td>
      <td>Park</td>
      <td>Bus Line</td>
      <td>Jewelry Store</td>
      <td>Trail</td>
      <td>Sushi Restaurant</td>
      <td>Event Space</td>
      <td>Ethiopian Restaurant</td>
      <td>Electronics Store</td>
      <td>Eastern European Restaurant</td>
      <td>Dumpling Restaurant</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Downtown Toronto</td>
      <td>1</td>
      <td>Café</td>
      <td>Bookstore</td>
      <td>Japanese Restaurant</td>
      <td>Bar</td>
      <td>Bakery</td>
      <td>Coffee Shop</td>
      <td>Restaurant</td>
      <td>Sandwich Place</td>
      <td>Pub</td>
      <td>Poutine Place</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Downtown Toronto</td>
      <td>1</td>
      <td>Coffee Shop</td>
      <td>Café</td>
      <td>Hotel</td>
      <td>Restaurant</td>
      <td>Steakhouse</td>
      <td>Gastropub</td>
      <td>Bar</td>
      <td>Gym</td>
      <td>Deli / Bodega</td>
      <td>American Restaurant</td>
    </tr>
    <tr>
      <th>30</th>
      <td>Downtown Toronto</td>
      <td>1</td>
      <td>Café</td>
      <td>Grocery Store</td>
      <td>Park</td>
      <td>Convenience Store</td>
      <td>Athletics &amp; Sports</td>
      <td>Italian Restaurant</td>
      <td>Baby Store</td>
      <td>Diner</td>
      <td>Restaurant</td>
      <td>Coffee Shop</td>
    </tr>
    <tr>
      <th>31</th>
      <td>West Toronto</td>
      <td>1</td>
      <td>Supermarket</td>
      <td>Discount Store</td>
      <td>Bakery</td>
      <td>Gym / Fitness Center</td>
      <td>Park</td>
      <td>Pharmacy</td>
      <td>Music Venue</td>
      <td>Middle Eastern Restaurant</td>
      <td>Café</td>
      <td>Brewery</td>
    </tr>
    <tr>
      <th>32</th>
      <td>West Toronto</td>
      <td>1</td>
      <td>Bar</td>
      <td>Café</td>
      <td>Restaurant</td>
      <td>Coffee Shop</td>
      <td>Vietnamese Restaurant</td>
      <td>Vegetarian / Vegan Restaurant</td>
      <td>Asian Restaurant</td>
      <td>Pizza Place</td>
      <td>Bakery</td>
      <td>French Restaurant</td>
    </tr>
    <tr>
      <th>33</th>
      <td>West Toronto</td>
      <td>1</td>
      <td>Coffee Shop</td>
      <td>Café</td>
      <td>Breakfast Spot</td>
      <td>Grocery Store</td>
      <td>Italian Restaurant</td>
      <td>Nightclub</td>
      <td>Performing Arts Venue</td>
      <td>Pet Store</td>
      <td>Climbing Gym</td>
      <td>Caribbean Restaurant</td>
    </tr>
    <tr>
      <th>34</th>
      <td>West Toronto</td>
      <td>1</td>
      <td>Café</td>
      <td>Mexican Restaurant</td>
      <td>Bar</td>
      <td>Grocery Store</td>
      <td>Antique Shop</td>
      <td>Bakery</td>
      <td>Cajun / Creole Restaurant</td>
      <td>Diner</td>
      <td>Fried Chicken Joint</td>
      <td>Arts &amp; Crafts Store</td>
    </tr>
    <tr>
      <th>37</th>
      <td>East Toronto</td>
      <td>1</td>
      <td>Yoga Studio</td>
      <td>Auto Workshop</td>
      <td>Comic Shop</td>
      <td>Park</td>
      <td>Pizza Place</td>
      <td>Butcher</td>
      <td>Burrito Place</td>
      <td>Restaurant</td>
      <td>Brewery</td>
      <td>Skate Park</td>
    </tr>
  </tbody>
</table>
</div>



Cluster 3


```python
Toronto_merged.loc[Toronto_merged['Cluster Labels'] == 2, Toronto_merged.columns[[1] + list(range(5, Toronto_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Borough</th>
      <th>Cluster Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>24</th>
      <td>Central Toronto</td>
      <td>2</td>
      <td>Café</td>
      <td>Coffee Shop</td>
      <td>Sandwich Place</td>
      <td>Pizza Place</td>
      <td>Liquor Store</td>
      <td>BBQ Joint</td>
      <td>Pub</td>
      <td>French Restaurant</td>
      <td>Martial Arts Dojo</td>
      <td>Burger Joint</td>
    </tr>
  </tbody>
</table>
</div>



Cluster 4


```python
Toronto_merged.loc[Toronto_merged['Cluster Labels'] == 3, Toronto_merged.columns[[1] + list(range(5, Toronto_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Borough</th>
      <th>Cluster Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>27</th>
      <td>Downtown Toronto</td>
      <td>3</td>
      <td>Airport Lounge</td>
      <td>Airport Service</td>
      <td>Airport Terminal</td>
      <td>Plane</td>
      <td>Harbor / Marina</td>
      <td>Boat or Ferry</td>
      <td>Airport</td>
      <td>Airport Food Court</td>
      <td>Airport Gate</td>
      <td>Sculpture Garden</td>
    </tr>
  </tbody>
</table>
</div>



Cluster 5


```python
Toronto_merged.loc[Toronto_merged['Cluster Labels'] == 4, Toronto_merged.columns[[1] + list(range(5, Toronto_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Borough</th>
      <th>Cluster Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>East Toronto</td>
      <td>4</td>
      <td>Café</td>
      <td>Coffee Shop</td>
      <td>American Restaurant</td>
      <td>Bakery</td>
      <td>Italian Restaurant</td>
      <td>Gastropub</td>
      <td>Yoga Studio</td>
      <td>Diner</td>
      <td>Park</td>
      <td>New American Restaurant</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Central Toronto</td>
      <td>4</td>
      <td>Bus Line</td>
      <td>Dim Sum Restaurant</td>
      <td>Park</td>
      <td>Swim School</td>
      <td>Falafel Restaurant</td>
      <td>Event Space</td>
      <td>Ethiopian Restaurant</td>
      <td>Electronics Store</td>
      <td>Eastern European Restaurant</td>
      <td>Dumpling Restaurant</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Downtown Toronto</td>
      <td>4</td>
      <td>Coffee Shop</td>
      <td>Japanese Restaurant</td>
      <td>Gay Bar</td>
      <td>Sushi Restaurant</td>
      <td>Burger Joint</td>
      <td>Restaurant</td>
      <td>Men's Store</td>
      <td>Café</td>
      <td>Bubble Tea Shop</td>
      <td>Mediterranean Restaurant</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Downtown Toronto</td>
      <td>4</td>
      <td>Coffee Shop</td>
      <td>Café</td>
      <td>Restaurant</td>
      <td>Hotel</td>
      <td>Clothing Store</td>
      <td>Gastropub</td>
      <td>Italian Restaurant</td>
      <td>Cosmetics Shop</td>
      <td>Cocktail Bar</td>
      <td>Park</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Downtown Toronto</td>
      <td>4</td>
      <td>Coffee Shop</td>
      <td>Café</td>
      <td>Italian Restaurant</td>
      <td>Sandwich Place</td>
      <td>Bar</td>
      <td>Bubble Tea Shop</td>
      <td>Burger Joint</td>
      <td>Japanese Restaurant</td>
      <td>Ice Cream Shop</td>
      <td>Falafel Restaurant</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Downtown Toronto</td>
      <td>4</td>
      <td>Coffee Shop</td>
      <td>Hotel</td>
      <td>Café</td>
      <td>Restaurant</td>
      <td>American Restaurant</td>
      <td>Steakhouse</td>
      <td>Italian Restaurant</td>
      <td>Deli / Bodega</td>
      <td>Gastropub</td>
      <td>Gym</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Downtown Toronto</td>
      <td>4</td>
      <td>Café</td>
      <td>Vegetarian / Vegan Restaurant</td>
      <td>Chinese Restaurant</td>
      <td>Bar</td>
      <td>Bakery</td>
      <td>Mexican Restaurant</td>
      <td>Vietnamese Restaurant</td>
      <td>Coffee Shop</td>
      <td>Dumpling Restaurant</td>
      <td>Grocery Store</td>
    </tr>
    <tr>
      <th>36</th>
      <td>West Toronto</td>
      <td>4</td>
      <td>Coffee Shop</td>
      <td>Pizza Place</td>
      <td>Café</td>
      <td>Sushi Restaurant</td>
      <td>Italian Restaurant</td>
      <td>Park</td>
      <td>Bookstore</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Indie Movie Theater</td>
      <td>Bar</td>
    </tr>
  </tbody>
</table>
</div>



Out of the 36 total postal codes, cluster 1 had one venue, cluster 2 had 25, cluster had 1, cluster 4 had 1, and cluster 5 had 8. The relative amount of venues, with more than 1 venue, was cluster 2 with 69% and cluster 5 with 22%.

# Atlanta

The image below shows an aerial view of the zip codes of Atlanta. Note the difference in density between this image and the starting image for Toronto. 

![Alt Text](https://github.com/wacky-bird/coursera_capstone_project/blob/Images/ATL-start.png "Starting Atlanta Zip Code Data")

To eliminate zero returns from the Foursquare API, a smaller area was chosen to guarantee at least of result. The locations of these remaining zip codes are shown in the next image.

![Alt Text](https://github.com/wacky-bird/coursera_capstone_project/blob/Images/ATL-cleaned.png "Cleaned Atlanta Data")

Using the example of downtown Atlanta, the image below shows 12 venues that are in the are the longitude and latitude corresponding with downtown Atlanta. All but one venue fall in line with two meeting lines which are close to 90 degrees of each other. 

![Alt Text](https://github.com/wacky-bird/coursera_capstone_project/blob/Images/ATL-specific.png "Downtown Atlanta Example")

## Examine the Clusters for Atlanta

For ease of comparison the clustering of Atlanta, and Edmonton was down with k=5. Below are the resulting clusters for Atlanta.

Cluster 1


```python
Atlanta_merged.loc[Atlanta_merged['Cluster Labels'] == 0, Atlanta_merged.columns[[1] + list(range(4, Atlanta_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Zip Code</th>
      <th>Cluster Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>30306</td>
      <td>0</td>
      <td>Deli / Bodega</td>
      <td>Yoga Studio</td>
      <td>BBQ Joint</td>
      <td>Burger Joint</td>
      <td>Boutique</td>
      <td>Coffee Shop</td>
      <td>Café</td>
      <td>Thai Restaurant</td>
      <td>Gift Shop</td>
      <td>Mexican Restaurant</td>
    </tr>
    <tr>
      <th>10</th>
      <td>30314</td>
      <td>0</td>
      <td>Pool</td>
      <td>Park</td>
      <td>Trail</td>
      <td>Tennis Court</td>
      <td>Doctor's Office</td>
      <td>Fast Food Restaurant</td>
      <td>Farmers Market</td>
      <td>Falafel Restaurant</td>
      <td>Event Space</td>
      <td>Event Service</td>
    </tr>
    <tr>
      <th>12</th>
      <td>30316</td>
      <td>0</td>
      <td>Cosmetics Shop</td>
      <td>Comedy Club</td>
      <td>Park</td>
      <td>Grocery Store</td>
      <td>Bakery</td>
      <td>Home Service</td>
      <td>Deli / Bodega</td>
      <td>Donut Shop</td>
      <td>Fast Food Restaurant</td>
      <td>Farmers Market</td>
    </tr>
  </tbody>
</table>
</div>



Cluster 2


```python
Atlanta_merged.loc[Atlanta_merged['Cluster Labels'] == 1, Atlanta_merged.columns[[1] + list(range(4, Atlanta_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Zip Code</th>
      <th>Cluster Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>30309</td>
      <td>1</td>
      <td>Music Venue</td>
      <td>Café</td>
      <td>Sandwich Place</td>
      <td>Coffee Shop</td>
      <td>Gym / Fitness Center</td>
      <td>Thai Restaurant</td>
      <td>Performing Arts Venue</td>
      <td>Shipping Store</td>
      <td>Monument / Landmark</td>
      <td>Restaurant</td>
    </tr>
    <tr>
      <th>1</th>
      <td>30303</td>
      <td>1</td>
      <td>Sandwich Place</td>
      <td>Coffee Shop</td>
      <td>Mexican Restaurant</td>
      <td>Event Space</td>
      <td>Deli / Bodega</td>
      <td>Fast Food Restaurant</td>
      <td>Café</td>
      <td>Caribbean Restaurant</td>
      <td>Lounge</td>
      <td>Falafel Restaurant</td>
    </tr>
    <tr>
      <th>2</th>
      <td>30304</td>
      <td>1</td>
      <td>American Restaurant</td>
      <td>Coffee Shop</td>
      <td>New American Restaurant</td>
      <td>Pharmacy</td>
      <td>Shipping Store</td>
      <td>Sporting Goods Shop</td>
      <td>Mexican Restaurant</td>
      <td>Breakfast Spot</td>
      <td>Shopping Mall</td>
      <td>Fast Food Restaurant</td>
    </tr>
    <tr>
      <th>3</th>
      <td>30305</td>
      <td>1</td>
      <td>Salon / Barbershop</td>
      <td>Italian Restaurant</td>
      <td>Gym</td>
      <td>Burrito Place</td>
      <td>Farmers Market</td>
      <td>Café</td>
      <td>Shipping Store</td>
      <td>Sandwich Place</td>
      <td>Chinese Restaurant</td>
      <td>Sushi Restaurant</td>
    </tr>
    <tr>
      <th>5</th>
      <td>30307</td>
      <td>1</td>
      <td>Pool</td>
      <td>Athletics &amp; Sports</td>
      <td>Golf Course</td>
      <td>Tennis Court</td>
      <td>Church</td>
      <td>Outdoor Sculpture</td>
      <td>Food Truck</td>
      <td>Basketball Court</td>
      <td>Park</td>
      <td>Playground</td>
    </tr>
    <tr>
      <th>6</th>
      <td>30308</td>
      <td>1</td>
      <td>Southern / Soul Food Restaurant</td>
      <td>Gay Bar</td>
      <td>Pizza Place</td>
      <td>New American Restaurant</td>
      <td>Nail Salon</td>
      <td>Coffee Shop</td>
      <td>Donut Shop</td>
      <td>Seafood Restaurant</td>
      <td>Martial Arts Dojo</td>
      <td>Brewery</td>
    </tr>
    <tr>
      <th>7</th>
      <td>30310</td>
      <td>1</td>
      <td>Brewery</td>
      <td>Food</td>
      <td>Gas Station</td>
      <td>Paper / Office Supplies Store</td>
      <td>Liquor Store</td>
      <td>Event Service</td>
      <td>Food Court</td>
      <td>Flower Shop</td>
      <td>Fast Food Restaurant</td>
      <td>Farmers Market</td>
    </tr>
    <tr>
      <th>8</th>
      <td>30312</td>
      <td>1</td>
      <td>American Restaurant</td>
      <td>Pizza Place</td>
      <td>Park</td>
      <td>Burger Joint</td>
      <td>Seafood Restaurant</td>
      <td>Coffee Shop</td>
      <td>Yoga Studio</td>
      <td>Mexican Restaurant</td>
      <td>Cemetery</td>
      <td>Scenic Lookout</td>
    </tr>
    <tr>
      <th>9</th>
      <td>30313</td>
      <td>1</td>
      <td>Aquarium</td>
      <td>Coffee Shop</td>
      <td>Fast Food Restaurant</td>
      <td>Museum</td>
      <td>Sandwich Place</td>
      <td>Gift Shop</td>
      <td>American Restaurant</td>
      <td>Hotel</td>
      <td>Sports Bar</td>
      <td>Basketball Stadium</td>
    </tr>
    <tr>
      <th>13</th>
      <td>30317</td>
      <td>1</td>
      <td>Spa</td>
      <td>Pet Store</td>
      <td>BBQ Joint</td>
      <td>Breakfast Spot</td>
      <td>Sports Bar</td>
      <td>Sandwich Place</td>
      <td>Juice Bar</td>
      <td>Flower Shop</td>
      <td>Coffee Shop</td>
      <td>Bar</td>
    </tr>
    <tr>
      <th>14</th>
      <td>30320</td>
      <td>1</td>
      <td>Hotel</td>
      <td>Gym / Fitness Center</td>
      <td>American Restaurant</td>
      <td>Museum</td>
      <td>Italian Restaurant</td>
      <td>Pharmacy</td>
      <td>Convenience Store</td>
      <td>Comic Shop</td>
      <td>Rental Car Location</td>
      <td>Coffee Shop</td>
    </tr>
    <tr>
      <th>15</th>
      <td>30322</td>
      <td>1</td>
      <td>Café</td>
      <td>Gym</td>
      <td>Food Court</td>
      <td>Park</td>
      <td>Concert Hall</td>
      <td>Mediterranean Restaurant</td>
      <td>Bookstore</td>
      <td>Museum</td>
      <td>Bakery</td>
      <td>College Academic Building</td>
    </tr>
    <tr>
      <th>17</th>
      <td>30326</td>
      <td>1</td>
      <td>Clothing Store</td>
      <td>Cosmetics Shop</td>
      <td>Accessories Store</td>
      <td>Women's Store</td>
      <td>Boutique</td>
      <td>Jewelry Store</td>
      <td>Sporting Goods Shop</td>
      <td>Bakery</td>
      <td>Department Store</td>
      <td>American Restaurant</td>
    </tr>
    <tr>
      <th>20</th>
      <td>30332</td>
      <td>1</td>
      <td>Fast Food Restaurant</td>
      <td>Restaurant</td>
      <td>Food Stand</td>
      <td>Chinese Restaurant</td>
      <td>Music Venue</td>
      <td>Sandwich Place</td>
      <td>Coffee Shop</td>
      <td>Baseball Field</td>
      <td>General Entertainment</td>
      <td>Café</td>
    </tr>
    <tr>
      <th>21</th>
      <td>30335</td>
      <td>1</td>
      <td>Sandwich Place</td>
      <td>Coffee Shop</td>
      <td>Fast Food Restaurant</td>
      <td>Mexican Restaurant</td>
      <td>Smoothie Shop</td>
      <td>Café</td>
      <td>Caribbean Restaurant</td>
      <td>Mediterranean Restaurant</td>
      <td>Falafel Restaurant</td>
      <td>Event Space</td>
    </tr>
    <tr>
      <th>22</th>
      <td>30354</td>
      <td>1</td>
      <td>Food</td>
      <td>Vineyard</td>
      <td>Video Store</td>
      <td>Lounge</td>
      <td>Trail</td>
      <td>Donut Shop</td>
      <td>Flower Shop</td>
      <td>Fast Food Restaurant</td>
      <td>Farmers Market</td>
      <td>Falafel Restaurant</td>
    </tr>
    <tr>
      <th>23</th>
      <td>30367</td>
      <td>1</td>
      <td>Coffee Shop</td>
      <td>Sandwich Place</td>
      <td>Hotel</td>
      <td>Music Venue</td>
      <td>Café</td>
      <td>Pizza Place</td>
      <td>Nightclub</td>
      <td>Lounge</td>
      <td>Gym / Fitness Center</td>
      <td>Performing Arts Venue</td>
    </tr>
  </tbody>
</table>
</div>



Cluster 3


```python
Atlanta_merged.loc[Atlanta_merged['Cluster Labels'] == 2, Atlanta_merged.columns[[1] + list(range(4, Atlanta_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Zip Code</th>
      <th>Cluster Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>19</th>
      <td>30330</td>
      <td>2</td>
      <td>Fast Food Restaurant</td>
      <td>Grocery Store</td>
      <td>Liquor Store</td>
      <td>Light Rail Station</td>
      <td>Yoga Studio</td>
      <td>Electronics Store</td>
      <td>Food</td>
      <td>Flower Shop</td>
      <td>Farmers Market</td>
      <td>Falafel Restaurant</td>
    </tr>
  </tbody>
</table>
</div>



Cluster 4


```python
Atlanta_merged.loc[Atlanta_merged['Cluster Labels'] == 3, Atlanta_merged.columns[[1] + list(range(4, Atlanta_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Zip Code</th>
      <th>Cluster Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>11</th>
      <td>30315</td>
      <td>3</td>
      <td>Southern / Soul Food Restaurant</td>
      <td>Fast Food Restaurant</td>
      <td>Discount Store</td>
      <td>Yoga Studio</td>
      <td>Donut Shop</td>
      <td>Flower Shop</td>
      <td>Farmers Market</td>
      <td>Falafel Restaurant</td>
      <td>Event Space</td>
      <td>Event Service</td>
    </tr>
    <tr>
      <th>18</th>
      <td>30329</td>
      <td>3</td>
      <td>Fast Food Restaurant</td>
      <td>Coffee Shop</td>
      <td>Optical Shop</td>
      <td>Mexican Restaurant</td>
      <td>Football Stadium</td>
      <td>Big Box Store</td>
      <td>Salon / Barbershop</td>
      <td>Burrito Place</td>
      <td>Indian Restaurant</td>
      <td>Doctor's Office</td>
    </tr>
  </tbody>
</table>
</div>



Cluster 5


```python
Atlanta_merged.loc[Atlanta_merged['Cluster Labels'] == 4, Atlanta_merged.columns[[1] + list(range(4, Atlanta_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Zip Code</th>
      <th>Cluster Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>16</th>
      <td>30324</td>
      <td>4</td>
      <td>Smoke Shop</td>
      <td>Residential Building (Apartment / Condo)</td>
      <td>Gay Bar</td>
      <td>Yoga Studio</td>
      <td>Donut Shop</td>
      <td>Fast Food Restaurant</td>
      <td>Farmers Market</td>
      <td>Falafel Restaurant</td>
      <td>Event Space</td>
      <td>Event Service</td>
    </tr>
  </tbody>
</table>
</div>



Of the 24 zip codes cluster 1 had 3 zip codes, cluster 2 had 17, cluster 3 had 1, cluster 4 had 2, and cluster 5 had 1. The relative percentage of zip codes in the greatest clusters were cluster 2 withe 71%, cluster 1 with 13%, and cluster 4 with 9%. 

## Edmonton

The clean up dataset of Edmonton neighbourhoods is shown in the image below. Note that the area is confined to a squared area in the center of the city. 

![Alt Text](https://github.com/wacky-bird/coursera_capstone_project/blob/Images/EDM-cleaned.png "Localized data points")

An example of how Foursquare explores, an example of its results shows 13 venues returned (image below). This venues range from provincial buildings to restaurants. This is a great exampled as to the distance that results are found from the geospatial coordinates obtained from the open data portal administered by the city of Edmonton.

![Alt Text](https://github.com/wacky-bird/coursera_capstone_project/blob/Images/EDM-downtown.png "Popular spot near downtown Edmonton")

Applying the same techniques as with the other cities, a cluster map was created showing the clustering of data in by cluster (colour), and geospatial information.

![Alt Text](https://github.com/wacky-bird/coursera_capstone_project/blob/Images/EDM-cluster.png "Cluster of Edmonton Data")

## Examine the Clusters for Edmonton

Cluster 1


```python
Edmonton_merged.loc[Edmonton_merged['Cluster Labels'] == 0, Edmonton_merged.columns[[0] + list(range(3, Edmonton_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Neighborhood</th>
      <th>Cluster Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>McIntyre Industrial</td>
      <td>0</td>
      <td>Insurance Office</td>
      <td>German Restaurant</td>
      <td>Clothing Store</td>
      <td>Thrift / Vintage Store</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Lendrum Place</td>
      <td>0</td>
      <td>Gym / Fitness Center</td>
      <td>Grocery Store</td>
      <td>Pizza Place</td>
      <td>Japanese Restaurant</td>
      <td>Sandwich Place</td>
      <td>Gastropub</td>
      <td>Liquor Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Parkallen</td>
      <td>0</td>
      <td>Bakery</td>
      <td>Yoga Studio</td>
      <td>Flea Market</td>
      <td>Gay Bar</td>
      <td>Gastropub</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Rossdale</td>
      <td>0</td>
      <td>Baseball Stadium</td>
      <td>Park</td>
      <td>Performing Arts Venue</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Flea Market</td>
      <td>Fish &amp; Chips Shop</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Windsor Park</td>
      <td>0</td>
      <td>Diner</td>
      <td>College Residence Hall</td>
      <td>Pub</td>
      <td>Ice Cream Shop</td>
      <td>Hotpot Restaurant</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Flea Market</td>
    </tr>
    <tr>
      <th>7</th>
      <td>River Valley Laurier</td>
      <td>0</td>
      <td>Zoo</td>
      <td>Theme Park Ride / Attraction</td>
      <td>Sports Club</td>
      <td>Park</td>
      <td>Electronics Store</td>
      <td>Flea Market</td>
      <td>Furniture / Home Store</td>
      <td>Dog Run</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Empire Park</td>
      <td>0</td>
      <td>Women's Store</td>
      <td>Cosmetics Shop</td>
      <td>Fast Food Restaurant</td>
      <td>Pharmacy</td>
      <td>South American Restaurant</td>
      <td>Department Store</td>
      <td>Ice Cream Shop</td>
      <td>Electronics Store</td>
      <td>Event Space</td>
      <td>Falafel Restaurant</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Strathearn</td>
      <td>0</td>
      <td>Bistro</td>
      <td>Movie Theater</td>
      <td>Coffee Shop</td>
      <td>Outdoors &amp; Recreation</td>
      <td>Café</td>
      <td>Yoga Studio</td>
      <td>Gastropub</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Westmount</td>
      <td>0</td>
      <td>Restaurant</td>
      <td>BBQ Joint</td>
      <td>Pet Store</td>
      <td>Thai Restaurant</td>
      <td>Café</td>
      <td>Salon / Barbershop</td>
      <td>Liquor Store</td>
      <td>Gourmet Shop</td>
      <td>Greek Restaurant</td>
      <td>Tea Room</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Coronet Addition Industrial</td>
      <td>0</td>
      <td>Convenience Store</td>
      <td>Thrift / Vintage Store</td>
      <td>Coffee Shop</td>
      <td>Flea Market</td>
      <td>Yoga Studio</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Lansdowne</td>
      <td>0</td>
      <td>Yoga Studio</td>
      <td>Athletics &amp; Sports</td>
      <td>Playground</td>
      <td>Clothing Store</td>
      <td>Furniture / Home Store</td>
      <td>Business Service</td>
      <td>Hotel</td>
      <td>Fish &amp; Chips Shop</td>
      <td>French Restaurant</td>
      <td>Ice Cream Shop</td>
    </tr>
    <tr>
      <th>14</th>
      <td>University of Alberta</td>
      <td>0</td>
      <td>Coffee Shop</td>
      <td>Pub</td>
      <td>Fast Food Restaurant</td>
      <td>Sandwich Place</td>
      <td>Theater</td>
      <td>College Gym</td>
      <td>Restaurant</td>
      <td>Café</td>
      <td>Shopping Mall</td>
      <td>College Theater</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Riverdale</td>
      <td>0</td>
      <td>Business Service</td>
      <td>Building</td>
      <td>Coffee Shop</td>
      <td>German Restaurant</td>
      <td>Gay Bar</td>
      <td>Gastropub</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
    </tr>
    <tr>
      <th>17</th>
      <td>River Valley Capitol Hill</td>
      <td>0</td>
      <td>Bakery</td>
      <td>Burger Joint</td>
      <td>Bank</td>
      <td>Yoga Studio</td>
      <td>Food &amp; Drink Shop</td>
      <td>Gay Bar</td>
      <td>Gastropub</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
    </tr>
    <tr>
      <th>18</th>
      <td>River Valley Walterdale</td>
      <td>0</td>
      <td>Coffee Shop</td>
      <td>Pizza Place</td>
      <td>Park</td>
      <td>Burrito Place</td>
      <td>Sandwich Place</td>
      <td>Fast Food Restaurant</td>
      <td>Gym / Fitness Center</td>
      <td>Japanese Restaurant</td>
      <td>Dessert Shop</td>
      <td>Café</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Grovenor</td>
      <td>0</td>
      <td>Park</td>
      <td>Electronics Store</td>
      <td>Miscellaneous Shop</td>
      <td>Pharmacy</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Allendale</td>
      <td>0</td>
      <td>Chinese Restaurant</td>
      <td>Hotpot Restaurant</td>
      <td>Board Shop</td>
      <td>Yoga Studio</td>
      <td>Flea Market</td>
      <td>Gastropub</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
    </tr>
    <tr>
      <th>22</th>
      <td>River Valley Whitemud</td>
      <td>0</td>
      <td>Farm</td>
      <td>Yoga Studio</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Gastropub</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Flea Market</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Laurier Heights</td>
      <td>0</td>
      <td>Park</td>
      <td>Athletics &amp; Sports</td>
      <td>Coffee Shop</td>
      <td>Construction &amp; Landscaping</td>
      <td>Yoga Studio</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
    </tr>
    <tr>
      <th>25</th>
      <td>River Valley Mayfair</td>
      <td>0</td>
      <td>General Entertainment</td>
      <td>Lake</td>
      <td>Golf Course</td>
      <td>Park</td>
      <td>Performing Arts Venue</td>
      <td>Falafel Restaurant</td>
      <td>Farm</td>
      <td>Farmers Market</td>
      <td>Event Space</td>
      <td>Fast Food Restaurant</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Downtown</td>
      <td>0</td>
      <td>Coffee Shop</td>
      <td>Hotel</td>
      <td>Sandwich Place</td>
      <td>Italian Restaurant</td>
      <td>Pub</td>
      <td>Indian Restaurant</td>
      <td>Café</td>
      <td>New American Restaurant</td>
      <td>Vegetarian / Vegan Restaurant</td>
      <td>Gastropub</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Bonnie Doon</td>
      <td>0</td>
      <td>Irish Pub</td>
      <td>Korean Restaurant</td>
      <td>French Restaurant</td>
      <td>Other Great Outdoors</td>
      <td>Theater</td>
      <td>Event Space</td>
      <td>Falafel Restaurant</td>
      <td>Electronics Store</td>
      <td>Farm</td>
      <td>Farmers Market</td>
    </tr>
    <tr>
      <th>34</th>
      <td>Strathcona</td>
      <td>0</td>
      <td>Theater</td>
      <td>Vietnamese Restaurant</td>
      <td>Train Station</td>
      <td>Park</td>
      <td>Mexican Restaurant</td>
      <td>Breakfast Spot</td>
      <td>Massage Studio</td>
      <td>Grocery Store</td>
      <td>Public Art</td>
      <td>Jazz Club</td>
    </tr>
    <tr>
      <th>35</th>
      <td>Davies Industrial West</td>
      <td>0</td>
      <td>Flea Market</td>
      <td>Yoga Studio</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Gastropub</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Fast Food Restaurant</td>
    </tr>
    <tr>
      <th>36</th>
      <td>Forest Heights</td>
      <td>0</td>
      <td>Vietnamese Restaurant</td>
      <td>Pilates Studio</td>
      <td>Yoga Studio</td>
      <td>Fast Food Restaurant</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Flea Market</td>
    </tr>
    <tr>
      <th>37</th>
      <td>McCauley</td>
      <td>0</td>
      <td>Grocery Store</td>
      <td>Gift Shop</td>
      <td>Korean Restaurant</td>
      <td>Bakery</td>
      <td>Café</td>
      <td>Yoga Studio</td>
      <td>Food &amp; Drink Shop</td>
      <td>Gastropub</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
    </tr>
    <tr>
      <th>38</th>
      <td>Queen Alexandra</td>
      <td>0</td>
      <td>Pub</td>
      <td>Coffee Shop</td>
      <td>Convenience Store</td>
      <td>Grocery Store</td>
      <td>Fish &amp; Chips Shop</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Flea Market</td>
    </tr>
    <tr>
      <th>39</th>
      <td>Glenora</td>
      <td>0</td>
      <td>Café</td>
      <td>Coffee Shop</td>
      <td>Food &amp; Drink Shop</td>
      <td>Yoga Studio</td>
      <td>Discount Store</td>
      <td>Gastropub</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
    </tr>
    <tr>
      <th>41</th>
      <td>Rosedale Industrial</td>
      <td>0</td>
      <td>Sports Bar</td>
      <td>Chinese Restaurant</td>
      <td>Grocery Store</td>
      <td>Coffee Shop</td>
      <td>Yoga Studio</td>
      <td>Food &amp; Drink Shop</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
    </tr>
    <tr>
      <th>43</th>
      <td>McQueen</td>
      <td>0</td>
      <td>Gym / Fitness Center</td>
      <td>Deli / Bodega</td>
      <td>Thrift / Vintage Store</td>
      <td>Hobby Shop</td>
      <td>Yoga Studio</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Flea Market</td>
    </tr>
    <tr>
      <th>45</th>
      <td>Mill Creek Ravine North</td>
      <td>0</td>
      <td>Playground</td>
      <td>Outdoors &amp; Recreation</td>
      <td>Yoga Studio</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Flea Market</td>
    </tr>
    <tr>
      <th>46</th>
      <td>Mill Creek Ravine South</td>
      <td>0</td>
      <td>Racetrack</td>
      <td>Fast Food Restaurant</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Flea Market</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Farmers Market</td>
    </tr>
    <tr>
      <th>47</th>
      <td>Ritchie</td>
      <td>0</td>
      <td>Music Venue</td>
      <td>Butcher</td>
      <td>Gastropub</td>
      <td>Coffee Shop</td>
      <td>Liquor Store</td>
      <td>Gay Bar</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
    </tr>
    <tr>
      <th>48</th>
      <td>Parkview</td>
      <td>0</td>
      <td>Scenic Lookout</td>
      <td>Park</td>
      <td>Deli / Bodega</td>
      <td>Grocery Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Flea Market</td>
      <td>Fish &amp; Chips Shop</td>
    </tr>
    <tr>
      <th>49</th>
      <td>Pleasantview</td>
      <td>0</td>
      <td>Park</td>
      <td>Paper / Office Supplies Store</td>
      <td>Yoga Studio</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Flea Market</td>
      <td>Fish &amp; Chips Shop</td>
    </tr>
    <tr>
      <th>54</th>
      <td>Holyrood</td>
      <td>0</td>
      <td>Playground</td>
      <td>Yoga Studio</td>
      <td>Fast Food Restaurant</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Flea Market</td>
      <td>Fish &amp; Chips Shop</td>
    </tr>
    <tr>
      <th>55</th>
      <td>Argyll</td>
      <td>0</td>
      <td>Park</td>
      <td>Climbing Gym</td>
      <td>Coffee Shop</td>
      <td>Thrift / Vintage Store</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
    </tr>
    <tr>
      <th>56</th>
      <td>Cromdale</td>
      <td>0</td>
      <td>Fast Food Restaurant</td>
      <td>Light Rail Station</td>
      <td>Bus Station</td>
      <td>Football Stadium</td>
      <td>Grocery Store</td>
      <td>Sandwich Place</td>
      <td>Flea Market</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Food Truck</td>
    </tr>
    <tr>
      <th>59</th>
      <td>River Valley Riverside</td>
      <td>0</td>
      <td>Golf Course</td>
      <td>Athletics &amp; Sports</td>
      <td>Home Service</td>
      <td>River</td>
      <td>Lawyer</td>
      <td>Yoga Studio</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
    </tr>
    <tr>
      <th>60</th>
      <td>Strathcona Junction</td>
      <td>0</td>
      <td>Chinese Restaurant</td>
      <td>Skating Rink</td>
      <td>Gym Pool</td>
      <td>Rental Car Location</td>
      <td>Coffee Shop</td>
      <td>Café</td>
      <td>Flea Market</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
    </tr>
    <tr>
      <th>61</th>
      <td>McKernan</td>
      <td>0</td>
      <td>Playground</td>
      <td>Grocery Store</td>
      <td>Yoga Studio</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Flea Market</td>
    </tr>
    <tr>
      <th>62</th>
      <td>River Valley Glenora</td>
      <td>0</td>
      <td>Café</td>
      <td>Museum</td>
      <td>Trail</td>
      <td>Coffee Shop</td>
      <td>Historic Site</td>
      <td>Flea Market</td>
      <td>Gastropub</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
    </tr>
  </tbody>
</table>
</div>



Cluster 2


```python
Edmonton_merged.loc[Edmonton_merged['Cluster Labels'] == 1, Edmonton_merged.columns[[0] + list(range(3, Edmonton_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Neighborhood</th>
      <th>Cluster Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>23</th>
      <td>Queen Mary Park</td>
      <td>1</td>
      <td>Nightclub</td>
      <td>Gym</td>
      <td>Burger Joint</td>
      <td>Karaoke Bar</td>
      <td>Convenience Store</td>
      <td>Mexican Restaurant</td>
      <td>Gastropub</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Boyle Street</td>
      <td>1</td>
      <td>Chinese Restaurant</td>
      <td>Vietnamese Restaurant</td>
      <td>Hotel</td>
      <td>Grocery Store</td>
      <td>Bar</td>
      <td>Yoga Studio</td>
      <td>Flea Market</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
    </tr>
    <tr>
      <th>31</th>
      <td>Avonmore</td>
      <td>1</td>
      <td>Fast Food Restaurant</td>
      <td>Convenience Store</td>
      <td>Thrift / Vintage Store</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Yoga Studio</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
    </tr>
    <tr>
      <th>33</th>
      <td>King Edward Park</td>
      <td>1</td>
      <td>Pizza Place</td>
      <td>Bus Station</td>
      <td>Bank</td>
      <td>Yoga Studio</td>
      <td>Flea Market</td>
      <td>Gastropub</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
    </tr>
  </tbody>
</table>
</div>



Cluster 3


```python
Edmonton_merged.loc[Edmonton_merged['Cluster Labels'] == 2, Edmonton_merged.columns[[0] + list(range(3, Edmonton_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Neighborhood</th>
      <th>Cluster Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>51</th>
      <td>Cloverdale</td>
      <td>2</td>
      <td>Music Venue</td>
      <td>Park</td>
      <td>Café</td>
      <td>Museum</td>
      <td>Ski Area</td>
      <td>Food &amp; Drink Shop</td>
      <td>Gastropub</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
    </tr>
  </tbody>
</table>
</div>



Cluster 4


```python
Edmonton_merged.loc[Edmonton_merged['Cluster Labels'] == 3, Edmonton_merged.columns[[0] + list(range(3, Edmonton_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Neighborhood</th>
      <th>Cluster Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>15</th>
      <td>Oliver</td>
      <td>3</td>
      <td>Lounge</td>
      <td>Pharmacy</td>
      <td>Coffee Shop</td>
      <td>Mediterranean Restaurant</td>
      <td>Café</td>
      <td>Diner</td>
      <td>Pizza Place</td>
      <td>Falafel Restaurant</td>
      <td>Restaurant</td>
      <td>Scenic Lookout</td>
    </tr>
  </tbody>
</table>
</div>



Cluster 5


```python
Edmonton_merged.loc[Edmonton_merged['Cluster Labels'] == 4, Edmonton_merged.columns[[0] + list(range(3, Edmonton_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Neighborhood</th>
      <th>Cluster Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>Malmo Plains</td>
      <td>4</td>
      <td>Playground</td>
      <td>Lake</td>
      <td>Yoga Studio</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Gastropub</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Central McDougall</td>
      <td>4</td>
      <td>Music Store</td>
      <td>Chinese Restaurant</td>
      <td>Vegetarian / Vegan Restaurant</td>
      <td>Coffee Shop</td>
      <td>Bakery</td>
      <td>Historic Site</td>
      <td>Sandwich Place</td>
      <td>Flea Market</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
    </tr>
    <tr>
      <th>11</th>
      <td>CPR Irvine</td>
      <td>4</td>
      <td>Chinese Restaurant</td>
      <td>Ice Cream Shop</td>
      <td>Sporting Goods Shop</td>
      <td>German Restaurant</td>
      <td>Burger Joint</td>
      <td>Restaurant</td>
      <td>Convenience Store</td>
      <td>Café</td>
      <td>Yoga Studio</td>
      <td>Food Truck</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Belgravia</td>
      <td>4</td>
      <td>Yoga Studio</td>
      <td>Light Rail Station</td>
      <td>Park</td>
      <td>Café</td>
      <td>Dog Run</td>
      <td>Hotel</td>
      <td>Fish &amp; Chips Shop</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Hazeldean</td>
      <td>4</td>
      <td>Bakery</td>
      <td>Breakfast Spot</td>
      <td>Yoga Studio</td>
      <td>Flea Market</td>
      <td>Gay Bar</td>
      <td>Gastropub</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
    </tr>
    <tr>
      <th>30</th>
      <td>Brookside</td>
      <td>4</td>
      <td>Park</td>
      <td>Soccer Field</td>
      <td>Home Service</td>
      <td>Yoga Studio</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Flea Market</td>
      <td>Fish &amp; Chips Shop</td>
    </tr>
    <tr>
      <th>32</th>
      <td>Crestwood</td>
      <td>4</td>
      <td>Café</td>
      <td>Italian Restaurant</td>
      <td>Bakery</td>
      <td>Bank</td>
      <td>Burger Joint</td>
      <td>Optical Shop</td>
      <td>Historic Site</td>
      <td>Food Truck</td>
      <td>Gay Bar</td>
      <td>Gastropub</td>
    </tr>
    <tr>
      <th>40</th>
      <td>Whitemud Creek Ravine North</td>
      <td>4</td>
      <td>Rest Area</td>
      <td>Ski Chalet</td>
      <td>Yoga Studio</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Flea Market</td>
    </tr>
    <tr>
      <th>42</th>
      <td>River Valley Kinnaird</td>
      <td>4</td>
      <td>Park</td>
      <td>Italian Restaurant</td>
      <td>Tapas Restaurant</td>
      <td>Yoga Studio</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Flea Market</td>
    </tr>
    <tr>
      <th>44</th>
      <td>Calgary Trail North</td>
      <td>4</td>
      <td>Grocery Store</td>
      <td>American Restaurant</td>
      <td>Chinese Restaurant</td>
      <td>Ice Cream Shop</td>
      <td>Fast Food Restaurant</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Sandwich Place</td>
      <td>Coffee Shop</td>
      <td>Furniture / Home Store</td>
      <td>Liquor Store</td>
    </tr>
    <tr>
      <th>50</th>
      <td>Coronet Industrial</td>
      <td>4</td>
      <td>Diner</td>
      <td>Print Shop</td>
      <td>Vietnamese Restaurant</td>
      <td>Chinese Restaurant</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
    </tr>
    <tr>
      <th>52</th>
      <td>River Valley Victoria</td>
      <td>4</td>
      <td>Italian Restaurant</td>
      <td>Cosmetics Shop</td>
      <td>Park</td>
      <td>Yoga Studio</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
    </tr>
    <tr>
      <th>53</th>
      <td>University of Alberta Farm</td>
      <td>4</td>
      <td>Ice Cream Shop</td>
      <td>Gym / Fitness Center</td>
      <td>Yoga Studio</td>
      <td>Fish &amp; Chips Shop</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
      <td>Flea Market</td>
    </tr>
    <tr>
      <th>57</th>
      <td>Garneau</td>
      <td>4</td>
      <td>Coffee Shop</td>
      <td>Café</td>
      <td>Fast Food Restaurant</td>
      <td>Pizza Place</td>
      <td>Vegetarian / Vegan Restaurant</td>
      <td>Indie Movie Theater</td>
      <td>Diner</td>
      <td>Japanese Restaurant</td>
      <td>Sandwich Place</td>
      <td>Lounge</td>
    </tr>
    <tr>
      <th>58</th>
      <td>North Glenora</td>
      <td>4</td>
      <td>Burrito Place</td>
      <td>Mexican Restaurant</td>
      <td>Yoga Studio</td>
      <td>General Entertainment</td>
      <td>Gastropub</td>
      <td>Furniture / Home Store</td>
      <td>French Restaurant</td>
      <td>Football Stadium</td>
      <td>Food Truck</td>
      <td>Food &amp; Drink Shop</td>
    </tr>
  </tbody>
</table>
</div>



With the greatest amount of neighbourhoods, 63, the clustering of data was still maintained at k=5. The number of neighbourhoods per cluster was 42 for cluster 1, 15 for cluster 5, 4 for cluster 2 and 1 for clusters 3 and 4 each. The relative percentage of these were 67%, 24%, and 6% respectively.

# Discussion

When looking at the clusters it's important to note that the cluster number is not important, but the amounts are. Looking at the percentage of venues in each cluster for each city we see a trend between all three cities in the the largest cluster percentage for Toronto, Atlanta, and Edmonton are 69%, 71%, and 67% respectively. The Toronto value, at 69%, is the mean of the three showing that both other cities are +/-2% of the mean. 

The more interesting result is for the second largest cluster. The relative amount of venues in the second largest clusters for Toronto, Atlanta, and Edmonton are 22%, 13%, and 24%, respectively. This shows that the Canadian cities are more similar in cluster amount that with Atlanta. A factor for this may be due to the low amount of zip codes that were available for Atlanta. But seeing as only a few zip codes had large numbers of venues recorded for Atlanta, it seems unlikely that a lot more options for zip code results offering unique findings would greatly increase the total amount of neighborhoods to cluster.

A visual look at the clustering isn't as dynamic as one would hope. One colour, purple is the dominant cluster while the others are either fringe or are small and some what scattered. A similar image to use would be like swiss cheese. Cluster 5 is mainly located around downtown Toronto. 

The dominant cluster, also purple, is has a bigger influence north of I20, while along the I20 to the south a combination of 3 clusters cuts off the bottom most of the purple coloured cluster. This separation is not like Toronto but this may in fact be an artifact of the lower number of data points on the plot.

Finally looking at Edmonton cluster map, the dominant cluster, red this time, is also present throughout the map as a whole. Cluster 2 has two small pockets which tie in with the smaller clusters and are located in the center north and eastern areas of Edmonton. Cluster 5 is only present twice in this area, showing that that cluster is geographically opposite to clusters 2-4. This partition gives closer to a 50/50 ratio in the southwestern corner of Edmonton. This clustering is more similar to that of Toronto.

Using both relative percentage of clustering and visualization it shows that Toronto is more similar to Edmoton than Atlanta.

### Recommendations

A limiting factor in this project was either the number of neighbourhoods or the venues throughout all neighbourhoods. To  do a thorough investigation a larger dataset is required. In the case of Edmonton, the number of neighbourhoods was not the limiting factor but more likely the lack of venues that have been registered on Foursquare. In the case of Atlanta it could quiet possibly be both the numbers of venues and zip codes to provide a more thorough look at the area.

A comparison between New York and Toronto was not what I wanted so I chose cities that had centroid data. If packages and scripts are available for neighbourhood geospatial determination then San Francisco would be one of the locations to use. This is assuming that features such as Golden Gate Park are taken into account as topographical and economical boundaries will alter habitation and business patterns.


# Conclusion

With this capstone project a comparison was done between Toronto and two other cities, Atlanta and Edmonton. The purpose of this project was to determine if Toronto is more similar to a semi-random American city, Atlanta, or to a semi-random Canadian city, Edmonton. Out of the 36 total postal codes in Toronto, cluster 1 had one neighbourhood, cluster 2 had 25, cluster had 1, cluster 4 had 1, and cluster 5 had 8. For Atlanta, of the 24 zip codes cluster 1 had 3 zip codes, cluster 2 had 17, cluster 3 had 1, cluster 4 had 2, and cluster 5 had 1.  Finally, for Edmonton the number of neighbourhoods per cluster was 42 for cluster 1, 15 for cluster 5, 4 for cluster 2 and 1 for clusters 3 and 4 each.

The relative amount of subdivisions, per cluster containing more than 1, for Toronto, Atlanta, and Edmonton was cluster 2 with 69%, cluster 5 with 22%; cluster 2 with 71%, cluster 1 with 13%, cluster 4 with 9%; and 67% for cluster 1, 24% for cluster 5, and 6% for cluster 2, respectively.

From the results of the clustering and location visualization it appears that Toronto is more similar to Edmonton than to Atlanta.
