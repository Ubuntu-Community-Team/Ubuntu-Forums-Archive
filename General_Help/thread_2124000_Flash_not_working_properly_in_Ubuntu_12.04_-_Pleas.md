---
title: "Flash not working properly in Ubuntu 12.04 - Please help !!"
date: 2013-03-09
forum: General Help
---

### Post by dkrises on 2013-03-09
Hi,

This seems to be a very common problem. Based on my search for solutions on the web, I tried many different things but still having problems. The working version of flash works only on youtube but is laggy. BBC news channel and iPlayer doesnot work; tried sites like rottentomatoes for movie trailers, but comes up with blank screens or freezes. 

I tried the following stuff:

[LIST]
[*]Installed Flash-Aid and tried with adobe flash stable, beta and 11.2 - didn't work;
[*]Installed flash plugin directly from the adobe website - still no luck; and
[*]I copied a version of 'flashplayer.so' to the 'usr\lib\adobeflash-plugin\' - only youtube works but is laggy
[/LIST]

Is there a workable solution for flash that is stable and works across many websites including BBC? It will be much appreciated.

dk

---

### Post by fiodev on 2013-03-09
Have you tried using Google Chrome?
[http://www.ubuntuupdates.org/ppa/google_chrome](http://www.ubuntuupdates.org/ppa/google_chrome) (website with instructions for installation).
Chromium will not work the same way. It has to be Chrome it is the only browser I know of that has Flash built into it.
Good luck!

---

### Post by fiodev on 2013-03-09
I have an idea for you:
1.) Open a terminal and type sudo -s (enter password at prompt)
2.) type: apt-get install flashplugin-installer

Ubuntu should take care of the rest for you. What browser are you using?

---

