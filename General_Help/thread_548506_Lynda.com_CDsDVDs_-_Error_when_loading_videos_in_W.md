---
title: "Lynda.com CDs/DVDs - Error when loading videos in Wine!"
date: 2007-09-11
forum: General Help
---

### Post by myacademy on 2007-09-11
Alright, so I've taken a shine to getting a handle on different scripting languages, software, concepts, etc. by means of Lynda.com lessons.
I have a ton of them on CD and DVD, and while they're fine to watch on my MacBook, sometimes I just want to sit at my desk and focus on my gigantic monitor.
I only run Linux on my desktop, so when I found that I can't watch the tutorials, I became bummed.
I launch WindowMode.exe with Wine, and this is what pops up in terminal...

fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\system32\\tmpDE300.FOT","C:\\windows\\temp\\AAX3e8.tmp",(null)): stub
fixme"wininet:InternetGetConnectedState always returning LAN connection
fixme"wininet:InternetGetConnectedState always returning LAN connection

The menu screen comes up right away, but as soon as I click on a particular tutorial to watch, an alert launches and tells me, "Script runtime error: Property not found."
My only option, of course, is OK.
Repeated clicking of this button yields no results, and when I kill the process, this is what pops up in terminal...

fixme:font:WineEngRemoveFontResourceEX :stub

I'm really not too keen on troubleshooting Wine errors, so if anyone could help me out (and others I'm sure), that would be awesome.

Oh yeah, I've checked other threads, used the (advanced) search feature, looked at the similar threads and scoped out the Wine app DB, all with no luck.

---

### Post by filologen on 2007-09-11
You could always just watch the individual videos in VLC (lynda.com normally (always?) organize them in folders which can be draged and dropped).

---

### Post by corrosione on 2007-11-21
i have the exact same issue.. thats what i have been doing playing the movies directly from the data folder..but it would be nice if it worked like it was suppose too

---

### Post by squideekie on 2008-05-24
Have you tried installing quicktime for windows in your wine programs directory? It sounds like wine is looking for the video codec to playback the video.

Only a hunch, let me know if it works...

---

