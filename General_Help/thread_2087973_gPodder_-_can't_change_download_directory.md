---
title: "gPodder - can't change download directory"
date: 2012-11-25
forum: General Help
---

### Post by grw on 2012-11-25
Can anyone tell me how to change the folder into which all my downloaded podcasts go in gPodder?

I have done in this in the past on Fedora. The instructions are here: [http://wiki.gpodder.org/wiki/User_Manual#Changing_the_downloads_folder_location](http://wiki.gpodder.org/wiki/User_Manual#Changing_the_downloads_folder_location) 

But now I can't find a setting with GPODDER_DOWNLOAD_DIR... It used to be there, I think. And I can't work out how to do it via command line.

Cheers...

---

### Post by grw on 2012-11-25
Clues?

---

### Post by rnerwein on 2012-11-26
> **grw said:**
> Clues?
try to set the path in: /etc/login.defs

if there is daemon running try the wanted path in: /etc/init
e.g.: aaaa.conf
and have a look in the proc filesystem:
cd /proc/PID
cat environ 
and look which path is set

---

