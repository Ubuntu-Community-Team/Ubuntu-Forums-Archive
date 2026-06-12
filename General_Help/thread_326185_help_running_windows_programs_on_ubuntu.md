---
title: "help running windows programs on ubuntu"
date: 2006-12-27
forum: General Help
---

### Post by dragnazz5.0 on 2006-12-27
alright, i need to figure out how to run this cd program that i have.  its made for windows but i know there is something out there that will allow me to use it.  if not than im just SOL.  but please someone help me figure this out.

---

### Post by Sef on 2006-12-27
[WINE]("http://winehq.com") may run it.   What program is it?

---

### Post by dragnazz5.0 on 2006-12-27
its a chassis program for drag cars.  i dont know if it has to run off the cd or if it will install.  i just cant run the setup.exe.  i tried wine but i dont think its installed correctly or i screwed something up.

---

### Post by bodhi.zazen on 2006-12-27
[http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by dragnazz5.0 on 2006-12-27
thanks guys....this is gonna be tough to figure out.  i dont understand any of it.

---

### Post by gh0st on 2006-12-27
Have you considered using a Windows Virtual Machine instead. It's not exactly installing your program on Linux and I suppose it's cheating a bit but hey if it works who cares. I have a Windows VM set up that I use for any complicated programs I can't get running in WINE.

You can get VMWare server for free from [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/) unfortunately you have to fill out a form to get a free serial number for it but it's pretty easy and they don't seem to hassle you with spam or anything. I signed up about 6 months ago and I've only had 1 email from VMware advertising a conference so far.

You have to install from the source TAR but it's easy to do. There are guides on the site, once you do that you can run the VMWare console and set up a new virtual machine an just stick an old version of windows on it. Works a treat for me. I try to stick to Linux but occasionally  I need to run a windows program and it's much quicker an easier than a dual-boot.

I also share my Linux files with the VM as a network drive using Samba.

Might be of some help to you, I dunno. You might not want to go down that route, I just thought I'd suggest it :)

---

### Post by dragnazz5.0 on 2006-12-27
thanks for the suggestion.  i got it to work for one of the programs but for some reason linux wont even read the other cd.  it gives me some error about not reading the file type or something.  kinda pisses me off actually

here is the error that i get

block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by dragnazz5.0 on 2006-12-28
well i got one of the programs running fine in WINE but the other cd wont even read.  can anyone give any insight into this or am i just sol?  thanks

---

