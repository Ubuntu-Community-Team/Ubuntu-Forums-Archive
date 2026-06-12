---
title: "Opera 9.50b1 crashing a lot on Ubuntu 8.04"
date: 2008-04-28
forum: General Help
---

### Post by Anonymoose on 2008-04-28
Hey, I just got Ubuntu up and running for the first time with my wireless nic and video drivers installed last night, but I've yet to reboot to see if it sticks. This is my first experience with linux so I'm not very accustomed with tinkering with config files and such, but hopefully I won't have to do that much. 

However, I'm not really sure if this is the right place to ask, but while trying to get flash player working for Opera, I had some trouble. Eventually I was told that the new Flash plug-in requires a GTK browser which Opera isn't but that the 9.50 beta is compatible. So I nabbed it and installed the nonfree flash plugin and it worked... Sorta. I've noticed that Opera's been crashing a lot, something that only seldom happened on Windows. I know this isn't a stable version, but still. If I were to say there's a pattern, it seems to happen mostly on flash sites, particularly when I try to interact. Without fail, clicking the download button on megaupload crashes the browser. I just tried to get something from sourceforge and it crashed. 

I was wondering if anybody has similar issues and/or knows of a possible fix? I'd appreciate any input, thanks.

---

### Post by TenPlus1 on 2008-04-28
Get the new Opera 9.50 Beta 2 and install that, but remove the old opera 1st using Synaptic Package manager and delete the hidden directory .opera in your home folder...

Also, Pop into the Tools menu, select Preferences, click advanced, content, plugin-options button and de-select all apart from flashplugin-nonfree...  

That should stop u crashing...

---

### Post by Anonymoose on 2008-04-29
Thanks, I'll give that a shot and report back if I see a difference I suppose. Anyone else gotten any success with this method? 

Edit: Just did it and tried to download something from megaupload with success. Hope it wasn't just a fluke. Thanks for the help.

---

