---
title: "My xubuntu stopped working"
date: 2012-12-28
forum: General Help
---

### Post by thorbs on 2012-12-28
I dont know what is wrong. But I started getting problems when I boot into my xubuntu desktop. I am getting a harddisk error. When I try to fix it, I get an error again about the tmp file failed.

I can no longer install any programs from ubuntu software center or use the software update manager.

When I but up from livedisc on usb it all works flawless.

Anybody who has suggestions to fix or do I need to install new again?

---

### Post by Bucky Ball on 2012-12-28
Hmm, this could point to hard drive failure as when you boot from USB you are using the USB, not the hard drive.

When booted from the USB, can you access files on the hard drive without issue or does that throw an error also?

Reinstall is a last resort and there must be an explanation if your install has suddenly stopped working. 

Have you done any updates/upgrades or installed anything and then this problem started happening?

---

### Post by thorbs on 2012-12-28
I seem to be able to access files without issues. 

I tried to unmount the harddrive and run a check and fix with the disk utility tool. But it returned the message that the disc had been scanned  but was not clean.

---

### Post by thorbs on 2012-12-29
I was able to fix the boot problem with the fsck command, after unmounting it. But I am still having problems when I try to sudo upgrade (or using the ubuntusoftware center).

I get the following error

 > W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/Release.gpg)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/precise-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/precise-getdeb/Release.gpg)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/source/Sources](http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/source/Sources)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/binary-amd64/Packages](http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/binary-amd64/Packages)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/binary-i386/Packages](http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/binary-i386/Packages)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/i18n/Translation-en_US](http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/i18n/Translation-en_US)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/i18n/Translation-en](http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/i18n/Translation-en)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/i18n/Translation-da](http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/games/i18n/Translation-da)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/binary-amd64/Packages](http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/binary-amd64/Packages)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/binary-i386/Packages](http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/binary-i386/Packages)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-en_US](http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-en_US)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-en](http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-en)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-da](http://archive.getdeb.net/ubuntu/dists/precise-getdeb/apps/i18n/Translation-da)  Unable to connect to archive.getdeb.net:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.


Any sugesstions how to fix it?

---

### Post by thorbs on 2012-12-29
fixed it by removing the get-deb repositories, they where offline.

---

### Post by Bucky Ball on 2012-12-30
All good, but ALWAYS run:

sudo apt-get update 

before: 

sudo apt-get upgrade

;)

You did the right thing unchecking the not working repos. They may just be offline for the moment or dead ...

---

### Post by Calinou on 2012-12-30
Slightly offtopic, but getdeb/playdeb are definitely dead since like 2 months. :P

---

