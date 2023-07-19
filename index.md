# Raspberry Pi Smart Mirror
In this project, I created a Smart Mirror using a Raspberry Pi 4. This device goes beyond the purpose of a normal mirror; it delivers updates on weather, news, art, and more, embedded subtly into the mirror’s code. In my portfolio, take a look at a mirror that not only you can admire yourself in, but update you on the world as well


```HTML 
<!--- This is an HTML comment in Markdown -->
<!--- Anything between these symbols will not render on the published site -->
```

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Yuju K | Stevenson | Aerospace Engineering | Incoming Junior


![Headstone Image](<img width="591" alt="Screen Shot 2023-07-19 at 11 09 26 PM" src="https://github.com/ykim79/BSE_Yuju_Portfolio/assets/138511348/f9add10d-4abe-4d9d-bd84-25fceed38fcd">
)
 
  # Final Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/QKRQ4_55l0A" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

- My third milestone was just to build everything around the smart mirror and setup the Raspberry Pi.
- I booted up the Pi and installed the OS, from which it promptly took me to a home page to setup all my code.
- I ran into a problem here as the SD card I put all of my code in was too small to take my whole VScode folder, so initially I was really worried, but fortunately, I still had my full config.js file, which meant all I had to do was manually reinstall each and every module, software and commands, just now on the Raspberry Pi itself. It really sucked, but at least I didn't start from square 1.
- I am happy to report that the reinstallation was a success! Now all that it is left to do is build the case and now my smart mirror is finished! The challenges presented to me in this final stretch and throughout the project were tough, but it was satisfying to overcome them all.
- The project gave me a sense of satisfaction and learning. It gave me insight on how the Raspberry Pi works, it's specific commands as well as how to write code for it and installing third-party modules. The project also helped my problem-solving skills, as whenever I encountered a problem, my reaction was not "What should I do" but rather "What can I do".

<img width="590" alt="Screen Shot 2023-07-19 at 11 13 36 PM" src="https://github.com/ykim79/BSE_Yuju_Portfolio/assets/138511348/56be545c-6bdc-4496-982d-090dcd7d8f36">


# Second Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/TOilmYLB7iM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

- My second Milestone was to incorporate at least 3 third-party modules for my smart mirror. I did this by updating my config.js file.
- I had to pull clones of third-party modules from GitHub in order to add them to my mirror, and I am glad to report that it was a huge success.
- My main grief with this part of the project had to be the installation itself for the modules, because when I added them to my modules folder, the app for MagicMirror2, Electron, would not launch and instead blast me with errors.
- The solution for this was to install the modules on both the modules folder of the smart mirror as well as on the main MagicMirror software itself. After I did this, Electron resumed working and everything worked well.

  <img width="547" alt="image" src="https://github.com/ykim79/BSE_Yuju_Portfolio/assets/138511348/d35cd742-3aeb-4602-b772-c0e7ddb7a450">

# First Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/no04TUmkrwU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


- My first milestone was to essentially just write the code in order to display the Magic Mirror. I managed to set up the code in order to display the default display of the Magic Mirror
- I had to install VScode in order to write this code as I do not have parts nor a Raspberry Pi as I write this because I am in Seoul, South Korea. Therefore, I am using a USB stick in order to house my Raspberry Pi OS, as well as a computer folder to house my code until my parts arrive.
- During this milestone, my main problem was finding out a solution in order to get a crucial part of the work finished even though I have no parts, and luckily I managed to run the software on my computer, leading to the completion of my first milestone.
- With this completion, I am starting to see that there are multiple ways to approach a rather unorthodox problem, and I hope I can keep solving these until the end.
- <img width="730" alt="image" src="https://github.com/ykim79/BSE_Yuju_Portfolio/assets/138511348/15da7b35-c062-4807-b641-4b003cb0ef7a">

# Schematics 
This is the basic image of a smart mirror

<img width="543" alt="image" src="https://github.com/ykim79/BSE_Yuju_Portfolio/assets/138511348/b867e283-0e32-4937-977d-64a386fd93ec">

# Code
This is my config.js code for my Magic Mirror
```python
let config = {
	address: "localhost",	
	port: 8080,
	basePath: "/",			
	ipWhitelist: ["127.0.0.1", "::ffff:127.0.0.1", "::1"],	
	useHttps: false, 		
	httpsPrivateKey: "", 	
	httpsCertificate: "", 	

	language: "en",
	locale: "en-US",
	logLevel: ["INFO", "LOG", "WARN", "ERROR"], 
	timeFormat: 24,
	units: "metric",

	modules: [
		{
			module: "alert",
		},
		{
			module: "updatenotification",
			position: "top_bar"
		},
		{
			module: "clock",
			position: "top_left"
		},
		{
			module: "calendar",
			header: "US Holidays",
			position: "top_left",
			config: {
				calendars: [
					{
						fetchInterval: 7 * 24 * 60 * 60 * 1000,
						symbol: "calendar-check",
						url: "https://ics.calendarlabs.com/76/mm3137/US_Holidays.ics"
					}
				]
			}
		},
		{
			module: "compliments",
			position: "lower_third"
		},
		{
			module: "weather",
			position: "top_right",
			config: {
				weatherProvider: "openweathermap",
				type: "current",
				location: "Monterey County",
				locationID: "5374376", 
				apiKey: "73541881cd59efd57ad6e242d7cf78b9"
			}
		},
		{
			module: "weather",
			position: "top_right",
			header: "Weather Forecast",
			config: {
				weatherProvider: "openweathermap",
				type: "forecast",
				location: "Monterey County",
				locationID: "5374376", 
				apiKey: "73541881cd59efd57ad6e242d7cf78b9"
			}
		},
		{
			module: "MMM-Bob-Ross",
			position: "bottom_left",
			config: {
			  imgHeight: "30vh",
			  videoHeight: "30vh",
			  updateInterval: 1*60*60*1000, 
			  autoPlay: true 
			}
		  }
	      ,{
			module: "MMM-Fuel",
			position: "bottom_right",
			config: {
				api_key: "73541881cd59efd57ad6e242d7cf78b9",
				lat: 36.595319,
				lng: -121.919567,
				types: ["gas"],
				
			}
		}
		,
		{
			module: "newsfeed",
			position: "bottom_bar",
			config: {
				feeds: [
					{
						title: "New York Times",
						url: "https://rss.nytimes.com/services/xml/rss/nyt/HomePage.xml"
					}
				],
				showSourceTitle: true,
				showPublishDate: true,
				broadcastNewsFeeds: true,
				broadcastNewsUpdates: true
			}
		},
		{
			
			module: 'MMM-WaterReminder',
			position: 'top_center',
			config: {
				foo: "Go get water you bastard",
				phrases: ["Water is a wonderful source of energy, go get some", "Drink water dumbass","Water time asshole.","'Drink water or else you'll have stones in your balls!'",
				"You see that glass of water over there? Drink it.","If you don't drink water, I will personally lobotomize you","Hey babe its 4pm, time for your next water break"],
				additionalPhrases: [],
				startTime: "00:00",
				endTime: "23:59",
				messageDuration: 1 * 60 * 1000, 
				animationSpeed: 4 * 1000, 
				reminderFrequency: 60 * 60 * 1000, 
				classes: "bright medium light",
				color: "#fff",
				idleMessage: "<br/>",
				logo: true,
				days: [0,1,2,3,4,5,6], 
				alarm: {
					status: false, 
					daysWithAudibleReminder: [1,2,3,4,5],
					src: "done-for-you.mp3",
					startTime: "09:00",
					endTime: "17:00",
				}
			}
		}
		
	]
};
if (typeof module !== "undefined") {module.exports = config;}
```





# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |

