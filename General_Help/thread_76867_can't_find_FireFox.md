---
title: "can't find FireFox"
date: 2005-10-15
forum: General Help
---

### Post by nicomazi on 2005-10-15
help people...i installed firefox 1.5 b2 and i can't find it anymore....where is it?

---

### Post by SqdnGuns on 2005-10-15
[QUOTE=nicomazi]help people...i installed firefox 1.5 b2 and i can't find it anymore....where is it?[/QUOTE]

Where did you install it??

---

### Post by nicomazi on 2005-10-15
[QUOTE=SqdnGuns]Where did you install it??[/QUOTE]
i downloaded it to home/softs folder. and using terminal unziped it into the same folder and installed it....
where did it installed itself i don't know..(or i wouldn't be asking this question)

---

### Post by mr_manny on 2005-10-15
Mine was a tar file...don't remember if it was originally compressed...

if it's a tar, you can check if there is a structure by using the test flag:
[me@server tars]$ tar tvf firefox-1.5b2.tar | more
drwxr-xr-x /                 0 2005-10-06 04:36:36 firefox/
-rw-r--r-- /                 0 2005-10-06 04:36:25 firefox/.autoreg
drwxr-xr-x /                 0 2005-10-06 04:36:29 firefox/chrome/
-rw-r--r-- /            566893 2005-10-06 04:36:25 firefox/chrome/en-US.jar
-rw-r--r-- /               834 2005-10-06 04:36:25 firefox/chrome/en-US.manifest
-rw-r--r-- /           1093929 2005-10-06 04:36:28 firefox/chrome/browser.jar
-rw-r--r-- /               431 2005-10-06 04:36:28 firefox/chrome/browser.manifest
-rw-r--r-- /            448972 2005-10-06 04:36:28 firefox/chrome/classic.jar
-rw-r--r-- /               322 2005-10-06 04:36:28 firefox/chrome/classic.manifest
-rw-r--r-- /             31967 2005-10-06 04:36:29 firefox/chrome/comm.jar
-rw-r--r-- /               144 2005-10-06 04:36:29 firefox/chrome/comm.manifest

when I untar the file, it will create a subdirectory called firefox.

I chose to install it under /usr/lib/firefox

I also created a plugins directory under /usr/lib and setup a link, that way you don't have to re-do your plugins for firefoxb3

[me@server firefox]$ pwd
/usr/lib/firefox

[me@server firefox]$ ll | grep plug
lrwxrwxrwx  1 root root      16 Oct  8 08:49 plugins -> /usr/lib/plugins
drwxr-xr-x  2 root root    4096 Oct  6 04:36 searchplugins

---

### Post by nicomazi on 2005-10-16
ok....i found it...but something really strange is going on.!!!!
i have now two firefoxes on my computer: version 1.0.4 and 1.5b2. they defenatly share database (history, bookmarks,passwords are all there from 1.0.4). but if i start firefox from application menie - 1.04 will start up. so if i want to run 1.5b2 i have to do it from install folder...
i thought that by installing new version of firefox it would just replace old one!!
what's up with that...

thnx

---

### Post by mr_manny on 2005-10-16
[me@server ~]$ whereis firefox
firefox: /usr/bin/firefox /usr/lib/firefox

the following shows a link to firefox under /usr/lib
[me@server ~]$ ll /usr/bin/firefox 
lrwxrwxrwx  1 root root 24 Jul 19 17:43 /usr/bin/firefox -> /usr/lib/firefox/firefox

I only have the b2 installed, previous version was manually removed.

---

