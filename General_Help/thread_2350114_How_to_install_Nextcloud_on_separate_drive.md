---
title: "How to install Nextcloud on separate drive?"
date: 2017-01-21
forum: General Help
---

### Post by alku1 on 2017-01-21
Hi all,

Im coming from a Windows environement feat. Seafile setup and my target is to setup nextcloud on ubuntu.
Beside my [AMD driver issue]("https://ubuntuforums.org/showthread.php?t=2349725")  everything runs well. The last thing missing is the seup of Nextcloud. Im following the official deployment guide and have read several how-tos online.
However, none of them highlights **how to install nextcloud or its database on a separate drive**.

I have setup a RAID array with Verycrypt container which is mounted to /media/veracrypt1. 
I would like to have at least the database (best case the whole nextcloud installation) on that drive. Im aware that the LAMP stack most probably needs to be on the main drive, but it shoudl be able to have the nextclod installation soemwhere else.

Surprisingly there seems to be no information out there on how to do it?!
Any hints?

EDIT: Sorry for the multiple threads. The forum went down during the posting process and I kept refreshing :(

---

### Post by TheFu on 2017-01-21
I would install everything using the default locations, then move the pieces to where you want them. 
apache/nginx --> /var/www/  (includes the php stuff)
mariadb/postgress/mysql --> /var/lib/mysql/ ..... 
NC data files --> configured during the install - I use /opt/nc-data/

If you fix all those places, that should be it, but I haven't done this myself.

If you want encryption, perhaps using the built-in dm-crypt/LUKS for Linux would be easier?  It would certainly be more secure for data at rest and better integrated into the OS for easier use.

I wouldn't use any storage that is mounted in /media/ - that area is for automatic mounts, not permanent mounts. If the intent is to have everything on a single disk, perhaps /opt/ would be a better place to mount that partition for your data?  

That's all the hints I've got.  Just work through moving each piece somewhere else. The web server and DB server are loosely coupled. The php settings control where the website is and the nc data setting controls where the individual data is located.

---

