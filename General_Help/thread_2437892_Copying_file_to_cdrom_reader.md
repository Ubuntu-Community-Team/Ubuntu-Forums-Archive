---
title: "Copying file to cdrom reader"
date: 2020-03-02
forum: General Help
---

### Post by torbentf on 2020-03-02
Hi,
A have a cdrom  reader  attached to a usb port and want to copy a file to blank dvd sitting in the cdrom  reader. When I use Nautilus the dvd just appears as Blank (and it is empty).
How do I do that in the terminal?
Best regards
torben

---

### Post by GhX6GZMB on 2020-03-02
Well, if it's just a CD-ROM reader, it won't be able to burn a CD. And it certainly won't handle DVDs. You need to tell us quite a bit more about your hardware.

---

### Post by torbentf on 2020-03-03
Hi,
It is:

Sandberg USB Mini DVD burner.

I can format it

torben@torben-Aspire-E5-773G:~$ dvd+rw-format -force /dev/sr0
* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.1.
* 4.7GB DVD+RW media detected.
* formatting 98.6|

lsblk gives:

......
sdb          8:16   0 931,5G  0 disk 
&#9492;&#9472;sdb1       8:17   0 931,5G  0 part /home/torben/torben/350D-ECB9
sr0         11:0    1   4,4G  0 rom

I want to do:

cp /home/torben/Downloads/lubuntu-18.04-alternate-i386.iso /?/?/?.....

torben

---

### Post by torbentf on 2020-03-03
Hi,
Maybe I should add that if I do ls I get:

torben@torben-Aspire-E5-773G:~$ ls /media
torben
 
If I do move I get:

torben@torben-Aspire-E5-773G:~$ sudo mv /home/torben/Downloads/torben /home/torben
mv: cannot stat '/home/torben/Downloads/torben': No such file or directory

Is something screwed up?
torben

---

### Post by torbentf on 2020-03-03
Hi,
Correction:

torben@torben-Aspire-E5-773G:~$ sudo mv /media/torben /home/torben
mv: cannot move '/media/torben' to '/home/torben/torben': Directory not empty
Sorry
torben

---

### Post by deadflowr on 2020-03-03
Install a burner program like xfburn or brasero
Ubuntu tutorial on burning the install to dvd:
[https://ubuntu.com/tutorials/tutorial-burn-a-dvd-on-ubuntu#1-overview]("https://ubuntu.com/tutorials/tutorial-burn-a-dvd-on-ubuntu#1-overview")

---

