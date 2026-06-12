---
title: "Firefox doesn't fully display embedded twitter timelines"
date: 2019-10-19
forum: General Help
---

### Post by ccor58 on 2019-10-19
I have a weather station web site at [http://tr0p0scatter.ca/html/wx-webcam.html](http://tr0p0scatter.ca/html/wx-webcam.html) . The bottom pane is the weather data message output. The top half is divided up to display a live webcam during stormy weather and three twitter timelines related to highway conditions during inclement weather as well as solar propagation conditions at any given time.

If I view it on firefox in a windows box the twitter timelines all auto display correctly, however, a couple or three updates back (not sure which one it was) firefox in the linux ubuntustudio 18.04 LTS stopped auto displaying the timelines and instead only displays them as html links. The linlks do work but open in a new tab or page and one has to click on each separately now.

Was there a change to ubuntu's included firefox package that did this? is there an option I need to adjust to have it return to displaying the embedded timelines correctly in automatic fashion?

thanks

---

### Post by uRock on 2019-10-19
When I go there, I see the twitter feeds. I am using 18.04, also. The first thing I would try would be closing Firefox, then going to the home folder and renaming .mozilla to .mozilla old, then opening Firefox to see if that page displays properly. If it works, then it is likely an extension/add-on causing the problem.

Edit: I just added a screenshot of what I see.

---

### Post by Holger_Gehrke on 2019-10-19
Works just fine for me on XUbuntu 18.04 with ff 69.0.2 **if **I temporarily disable my adblocker which probably considers executing twitter-scripts as some kind of tracking (and of course I have to whitelist script execution in NoScript, as expected for a site I haven't visited before). If I leave the blocker running I don't even get links, there's just nothing there except a message stating that the webcam is only operating during inclement weather.

Holger

---

### Post by ccor58 on 2019-10-19
That did the trick. Thanks guys.

---

