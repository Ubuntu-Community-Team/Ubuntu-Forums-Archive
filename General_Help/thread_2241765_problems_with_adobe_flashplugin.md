---
title: "problems with adobe flashplugin"
date: 2014-08-28
forum: General Help
---

### Post by alopex38 on 2014-08-28
I am running ubuntu 12.04 and use both Firefox and Chromium web browsers.

I have no trouble accessing bbc iplayer in Firefox - but when I try to do this in Chromium I am instructed to install Adobe flashplayer plug in  EVEN THOUGH IT IS ALREADY ON MY SYSTEM.

Any ideas as to why this might be?


Thanks in advance for any advice/help


Hippocrat

---

### Post by vasa1 on 2014-08-28
Because the latest Chromium stable can no longer use the same plugin that Firefox uses. You'll need to install something called pepper flash from the repository. To do so, type **sudo apt-get install pepperflashplugin-nonfree** in a terminal and hit **enter** or search the software center for pepper flash!

---

