---
title: "issue with dvd viewing on ubuntu 704"
date: 2007-06-02
forum: General Help
---

### Post by wickyman on 2007-06-02
I am somewhat of a newcomer to linux. I have used various distros of linux in the past for specialized applications, such as a streaming media server for my network or using various live cds (mostly slax) with usb drives to run my folding at home farm of servers, but until now ive never really considered using any distro as a complete desktop replacement for windows. After having issues with windows xp on my workstation I have decided to give ubuntu a try as its support base seems to be among the best around. But I am having some issues that I can not figure out a solution too.

My problem currently is that I can not view any dvd movies. I am, of course, talking about legitimate dvd movies that I have purchased from the store, not some downloaded iso. After searching the web (and portions of these forums) I came accross a few possible solutions, and one post pointed me towards some libraries that I may need (including libdvdcss, libdvdread, libdvdnav, and libdvdplay and others that escape my mind right now) as well as posts suggesting xine and mplayer as a viewer, but none of these solutions have helped.

The device is an Aopen DVD RW IDE drive, and when ever I insert a dvd movie, I receive a "blank cd inserted" message, as if I placed a blank cd in the drive that I was going to burn files. Data cds or dvds detect fine and I am able to read/use the data on the disks.

Any help would be appreciated.

---

### Post by mrcbrown on 2007-06-02
I setup my box with this:

[http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04](http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04)

Saved me the time of searching for all the replacements I wanted/needed - and got my DVD playing working without a hitch, might be of help to you too.

---

### Post by daschmidty on 2007-06-02
It is likely an issue with a non-free codec you need to play the dvds. the simplest soltuion is to add in the medibuntu unofficial repository 
Howto link: [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

and then do
```
sudo apt-get install lidvdcss2
```
that has worked for me in the past.

---

### Post by wickyman on 2007-06-03
Thank you both for your help, unfortunately it seems neither solutions managed to get my dvds to work, it seems the problem may be hardware related. I was reluctant to make that assumption but after trying so many things without result I am thinking I will just swap out the drive when the new motherboard arrives. 

I always learn a lot when im forced to trouble shoot and this has been no exception, I just hope that once i replace the board and the drive that my problems will be solved.

---

