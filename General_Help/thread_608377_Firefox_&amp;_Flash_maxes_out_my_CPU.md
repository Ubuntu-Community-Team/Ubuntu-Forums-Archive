---
title: "Firefox &amp; Flash maxes out my CPU"
date: 2007-11-09
forum: General Help
---

### Post by Stoffer on 2007-11-09
I've had this problem forever with Firefox.

Every time I run any flash application, such as flash videos, my CPU is consistently at 100% usage, which not only makes the videos skip all the time, but heats up the processor.  Upgrading from Fiesty to Gutsy didn't help, and I'm running FIrefox 2.0.0.8.  

Does anyone know the cause and/or solution to this issue?

---

### Post by gsiliceo on 2008-05-04
I recommend you to install the 9,048 flash player, it is a LOT less cpu intensive.
First test your current version of flash here
[COLOR="Blue"][SHow my flash player version]("http://www.mediacollege.com/adobe/flash/player/version/show.html")[/COLOR]
Then normally you'd have to download a 94 meg package that adobe provides with lots of flash player version but i'd make it easier for you uploading just the recommended 9.048.
[COLOR="Blue"][Download it here 2.5 megs to your desktop]("http://www.mediafire.com/?znhecmwx0j4")[/COLOR]

Close firefox.

Then extract it, right click on the package and *"extract here"*
Open the folder and copy the file libflashplayer.so 
Now open a terminal and do this
> sudo nautilus
Once is opened go to /usr/lib/flashplugin-nonfree/
And paste the file you just copied, replace when asked. 
Then go back to the extracted folder in your desktop and double click the flashplayer-installer, and choose execute in terminal, then hit enter and you are done.

Test your new version of flash.

Also try disabling powernowd, some people complaing that it slows down their cpu.

---

