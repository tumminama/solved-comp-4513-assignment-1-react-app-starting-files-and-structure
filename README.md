Download Link: https://assignmentchef.com/product/solved-comp-4513-assignment-1-react-app-starting-files-and-structure
<br>



<strong> </strong>Requirements

<ol>

 <li>You must make use of the create-react-app starting files and structure. You must deploy a production build of the application to your live server; the development version must be on GitHub. The filename for your starting file should be html (create-react-app does this automatically).</li>

 <li>This assignment consists of three main views (remember this is a single-page application, so it is best to think of the assignment consisting of different views). In the remainder of this assignment, I have provided a sketch of the basic layout of each view (some views have multiple subviews).</li>

</ol>

These sketches do not show the precise styling (or even the required layout); rather they show functionality and content. I will be expecting your pages to look significantly more polished and attractive than these sketches! A lot of the 23% design mark will be based on my assessment of how much effort you made on the styling and design.

You can change the layout if you wish. If you want your movie list to be horizontal on the bottom and the favorites to be vertical on the right, you can do so if you think that would be best … though I may not necessarily agree about the usability of your choices. I’d rather see you try something different in the layout/design than simply slap together something that is just a slightly improved version of the layout in my sketches.

<ol start="3">

 <li>If you’ve used JS or CSS that you’ve found online, I expect you to indicate that in your documentation and in the About view. Be sure to provide a URL of where you found it in the documentation. Failure to do so might result in a zero mark, so give credit for other people’s work!</li>

</ol>

<strong>             </strong>

<h1>Home View</h1>




<ol start="4">

 <li>When your assignment is first viewed, it should display the Home View. It consists of a hero image (and image that fills the entire browser width or up to a specific very wide value, say 1800 or 2200 pixels). You could use unsplash.com as a source for your image, but be sure to provide credit information somewhere on this page. In the middle of the page should be another rectangle with a place where the user can enter a title search string, as well as two buttons. Both will take the user to the Default View. If the first is clicked, then the movie list will be filtered on the movie title; if the second is clicked all the movies will be displayed.</li>

 <li>You must include some type of CSS transition and animation effect on this page. The more interesting it is, the more marks to be gained. I would also like you to use react-transition-group for this effect. See <a href="https://reactjs.org/docs/animation.html">https://reactjs.org/docs/animation.html</a> for more information.</li>

</ol>







<h1>Default View</h1>

<strong> </strong>

This view should be broken down into a lot of different hierarchical components. Remember: the reason we are using React is that it allows us to break a complex application down into smaller components.

<ol start="6">

 <li><strong>Header</strong>. The header should have a logo and a link/button to an About dialog. The logo should return to the Home View.</li>

 <li><strong>Movie List / Matches</strong>. Displays a list of movies. The URL for the API is:</li>

</ol>




http://www.randyconnolly.com/funwebdev/3rd/api/movie/movies-brief.php?id=ALL




The movie list should initially be sorted alphabetically on title. Initially, display all movies or filtered by name depending on what happened on the Home View. The Title, Year, and Rating column headings should be clickable: when clicked they sort the movies by that field. The blue boxes represent small poster images (see below for more info).




The API will take some time to retrieve this data. Display a loading animation (there are many free animated GIF available) until the data is retrieved. Simply display the image just before the fetch and then hide it after fetch is successful.




Clicking on the View button, the title, or the poster image will take the user to the <strong>Movie Details</strong> view. Be sure to set the mouse cursor to indicate they are clickable.




To improve the performance of your assignment, you must store the content retrieved from the movies-brief API in local storage after you fetch it. Your page should thus check if movie data from this API is already saved in local storage: if it is then use it, otherwise fetch it and store it in local storage. This approach improves initial performance by eliminating an early fetch in future uses of the application. Be sure to test that your application works when local storage is empty before submitting (you can empty local storage in for instance Chrome via the Application tab in DevTools).

<ol start="8">

 <li>Clicking on the Heart button will add the movie to the Favorites list. When a movie is added to the favorites list, a small poster image for it should be added to the list (be sure to set both the title and alt attributes to the movie title). The Favorites list should be hide-able. If the user clicks on the small poster image in the favorites list, it should switch to <strong>Movie Details</strong> view for that movie. When hovering over the poster image in the favorites list, it should display some type of close/delete icon.</li>

</ol>




When the user clicks on the Close icon, remove the photo from the list (and from state). The best way to implement this is to implement the Close icon as an image (or use just CSS transforms) and position in upper right. Use CSS :hover selector to change its opacity or visibility. If you want to always display the close button, that’s fine but there should be some type of state change on hover (e.g., change button opacity, or color, or size).




Clicking on the close button must remove the photo from favorites in state. Ideally, there will be some type of animation/transition on the Photo Thumb box to provide visual feedback that the photo is being deleted. Also, a movie can only be added once to favorites.

<ol start="9">

 <li>When the user selects the About link/button, it should display some type of modal dialog/window with information about assignment. Include group members, github link, technology used, any thirdparty source code, etc. Sometimes it makes sense to make use of existing components rather than re-invent the wheel. It is important to know how to integrate existing components. Thus here you <strong>must</strong> make use of an existing React modal-dialog component (e.g., react-modal or react-modaldialog).</li>

 <li>The movie poster images can be found in different sizes via the image server for tmdb.org (https://image.tmdb.org/t/p/). One of the data fields for each movie is poster, which contains the filename for the poster. You can then specify the image width you want by adding either w92, w154, w185, w342, w500, or w780 to the URL. For instance, for the movie with id=1144, the poster field value is “/wOBKAoUJZb5qTsWv5XXvVV2vUzz.jpg”. Thus to get a small thumbnail image (width = 92 pixels) of the poster, then the URL would be:</li>

</ol>




https://image.tmdb.org/t/p/w92/wOBKAoUJZb5qTsWv5XXvVV2vUzz.jpg




<ol start="11">

 <li><strong>Movie Filters</strong>. Allow the user to easily filter the list of movies. User should be able to find movies whose title contains anywhere within it whatever was entered into the title input box. The user should be able to filter the movie list by the release date year. They should be able to specify either: movies before a year, after a year, or between two years. Similarly the user should be able to filter the movie list by the average rating by also specifying a below, above, or between value. Also provide way to remove filters (that is, return to all movies being displayed). When the user clicks the filter button, the movie list should update.</li>

</ol>




If no matching movies are found, notify the user within the Movie List/Matches area.




The list of movies should scroll while the rest of the page stays. You can do this easily with the CSS overflow property.




These filters are not mutually exclusive. For instance, a user should be able to search for movies with the word “car” in it with a release year between 1990 and 2000 and a rating above 4.




The user should be able to toggle the visibility of the filters panel (though initially should be visible). Don’t be scared of using icons instead of text. There must be some type of transition effect (e.g., animation or fade), rather than just instantaneous visible/invisible.

<h1>Movie Details View</h1>




<ol start="12">

 <li><strong>Movie Details</strong>. Displays detailed information for the selected movie. The movie details can be retrieved from another API whose URL is (where xxxx is the id of the movie):</li>

</ol>




http://www.randyconnolly.com/funwebdev/3rd/api/movie/movies.php?id=XXXX




I would recommend running a test query in the browser with an ID of 1144 so that you can see the data and its structure. Note: do <strong>not</strong> store the results from this API in localstorage.




The API will take some time to retrieve this data. Display a loading animation until the data is retrieved. Simply display the image just before the fetch and then hide it after fetch is successful.




I expect this data to be nicely formatted and laid out sensibly. I have put the info here in three columns just to make it fit in Word. You can construct your layout anyway you’d like.




Working IMDB and TMDB links can be constructed from their related ID fields (e.g.

https://www.themoviedb.org/movie/xxxx and https://www.imdb.com/title/yyyy,

where xxxx is the tmdb_id field and yyyy is the imdb_id field)




The Close button will return user to the Default View. The Add to Favorites will add movie to favorites list.




The average rating is a value between 0 and 10. Create a component that displays the appropriate number of filled, empty, or half-star icons, using free font-awesome icons. Round the average to nearest half number (e.g., 5.2 round to 5, 5.4 round to 5.5, 5.8 round to 6).




<ol start="13">

 <li><strong>Cast and Crew</strong>. In the sketch above, Cast and Crew are shown as tabs, though you could use hide / show boxes as well. The Cast tab (it should be showing by default) will show the character name (in the movie) and the actor’s name (in real-life).</li>

</ol>




Sort the cast members by the order field. For the Crew tab, show the department, job, and name fields. Sort by department and then by name.




For the cast members, also display a View button. Clicking on it will take the user to <strong>Cast View</strong>.

<ol start="14">

 <li><strong>Poster Image</strong>. Display the poster using either w185 or w342 size. When the user clicks on the poster, display a larger version (w500 or w780) as a pop-up modal window. This is sometimes referred to as a lightbox effect. Use the same modal component that you used for the About information.</li>

</ol>




<h1>Cast View</h1>




<ol start="15">

 <li>Cast View replaces the movie specific information with more information about the selected cast member. Clicking Close Cast View will hide this new cast information (that is, return to Movie Details View).</li>

</ol>




This information will be retrieved from the TMDB API, which will require registering at https://www.themoviedb.org/. You either immediately get an API key when you register or you have to request one (I can’t remember, it’s been a long time since I had mine). The API key is under your profile settings for the site.




When you retrieve information about a movie from www.randyconnolly.com/funwebdev/3rd/ api/movie/movies.php, each object in the cast array has the following structure:

{

“cast_id”: 4,

“character”: “Chili Palmer”,

“credit_id”: “52fe43cbc3a36847f8070361”,

“gender”: 2,

“id”: 8891,

“name”: “John Travolta”,

“order”: 0

}




The id property will be used to make a person request from the tmdb API. For instance, a person request for John Travolta will look like:

https://api.themoviedb.org/3/person/<em>8891</em>?api_key=<em>[your API key]</em>

This will return a JSON object containing various information fields. I would like you to display birthday, biography, place of birth, and their IMDB link (using https://www.imdb.com/name/yyyy, where yyyy is the imdb_id field). For some cast members these fields will be empty, so handle that gracefully.

This JSON object also contains a profile_path property, which is a image of the cast member. You construct the request the same as with the movie posters, except the only size is w185.




<strong> </strong>