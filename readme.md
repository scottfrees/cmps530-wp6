# Weekly Project 6
This week's project is a re-hash of weekly project #2 - where we analyized movie rating data to answer the questions repeated below.  **The key difference** this week is that you should leverage `pandas` - and dispense with all the work we did to shape the data using dictionaries and classes.  In many ways, `pandas` removed the necessity for all this work - although in larger analyses you will benefit from a blend of approaches.

**Unlike in WP-2**, don't output your results in json/csv files - instead, develop your analysis directly in a **jupyter notebook** - which is a more convenient way to present your findings.

Importantly - your answers should match up exactly with what you found in the past analysis!  `pandas` is a tool - but it doesn't change the outcome.

## Some Recommendations
The data for movies is contained in three csv files - movies, ratings, and tags.  Use `read_csv` to load them as data frams.

Just as before, the movies `csv` file stores data in a suboptimal way - embedding the year within the title, and storing genre as a `|` delimited list - which isn't easy to work with.  I recommend you use the `apply` method to create new columns in the movies data frame, so you can have a genre (proper) list, along with a cleaned title column and new year column

The key that relates all the data is `movieId` - I recommend you look to merge / join these so you can interact with one `pandas` data frame.  You'll find the `merge` method usefull for this.

Merging movies and tags won't be much of an issue - but if you try to merge movies with ratings, its likely you'll run out of memory - there are a lot of ratings!  Thankfully, your analysis doesn't really need all the ratings - all the questions we ask revolve around the average rating for a movie, and the total number of ratings.  I recommend you use the `groupby` and `agg` functions to create a condensed list of ratings - where each movie occupies a single row and has the average and total count of ratings.  **This frame can be merged with the movies/tags easily**.  **`groupby` and `agg` are critical methods for data analysis - rely on them!

The analysis questions require sorting, make sure you take a look at `sort_values` as necessary.

### Part 1: Average Ratings and Number of Genres
Some movies have no genres, others have one, and others have many assigned to them.  Group movies into categories based on the number of genres assigned to them (i.e. 0, 1, 2, 3,....) and compute the **average** rating of movies in each category. 

**Important**:  If there are 5 movies that have 2 genres (for example), to compute the average rating for movies  with 2 genres, I want you to average the 5 average ratings found in the 5 movies.  This is different than simply averaging all the ratings - as some movies have a lot more ratings than others.  

### Part 2:   Top Rated Tags
Most movies have tags associated with them.  Calculate the average movie rating for each tag.  Calculate average rating using the same method as in Part 1 - take the average of the average ratings on each movie.  Filter the data so include only tags which were associated with 100 or more movies (which have ratings), and output the top 20 tags to your notebook, sorted (highest to lowest) by average rating.


### Part 3:  Frequently Rated Movies
Filter movies to include only movies with at least 10,000 ratings.  Sort the movies by average rating (highest to lowest), year (recent first), and then alphabetically, and output to your notebook.


