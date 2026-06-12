---
title: "Writing to blank dvds issue"
date: 2013-08-03
forum: General Help
---

### Post by chambogorden on 2013-08-03
Okay so I am getting an issue writing anything to a dvd through Ubuntu, when a dvd with media already on it is in, it reads the media fine, but still is unable to write at all to said dvd. After some poking about on the internet I found what I think might be the issue-my settings on info in /proc/sys/dev/cdrom/ which are as follows:

CD-ROM information, Id: cdrom.c 3.20 2003/12/17

drive name:        sr0
drive speed:        24
drive # of slots:    1
Can close tray:        1
Can open tray:        1
Can lock tray:        1
Can change speed:    1
Can select disk:    0
Can read multisession:    1
Can read MCN:        1
Reports media changed:    1
Can play audio:        1
Can write CD-R:        0
Can write CD-RW:    0
Can read DVD:        1
Can write DVD-R:    0
Can write DVD-RAM:    0
Can read MRW:        0
Can write MRW:        0
Can write RAM:        0

now it looks like simply changing some values would solve my problem and nenable me to write to the dvd, but /proc/sys/dev/cdrom/ needs root permission to be able to be modified, and various methods through terminal have only given me this:

avanti@avanti-Latitude-E6400:/proc/sys/dev/cdrom$ sudo chown -R avanti:avanti /proc/sys/dev/cdrom/info chown: changing ownership of ‘/proc/sys/dev/cdrom/info’: Operation not permitted
avanti@avanti-Latitude-E6400:/proc/sys/dev/cdrom$ chgrp avanti /proc/sys/dev/cdrom
chgrp: changing group of ‘/proc/sys/dev/cdrom’: Operation not permitted
avanti@avanti-Latitude-E6400:/proc/sys/dev/cdrom$ sudo chgrp avanti /proc/sys/dev/cdrom
chgrp: changing group of ‘/proc/sys/dev/cdrom’: Operation not permitted
avanti@avanti-Latitude-E6400:/proc/sys/dev/cdrom$ sudo rm -r /proc/sys/dev/cdrom/
rm: cannot remove ‘/proc/sys/dev/cdrom/autoclose’: Permission denied
rm: cannot remove ‘/proc/sys/dev/cdrom/autoeject’: Permission denied
rm: cannot remove ‘/proc/sys/dev/cdrom/check_media’: Permission denied
rm: cannot remove ‘/proc/sys/dev/cdrom/debug’: Permission denied
rm: cannot remove ‘/proc/sys/dev/cdrom/info’: Permission denied
rm: cannot remove ‘/proc/sys/dev/cdrom/lock’: Permission denied
avanti@avanti-Latitude-E6400:/proc/sys/dev/cdrom$ sudo nautilus

(nautilus:12733): IBUS-WARNING **: The owner of /home/avanti/.config/ibus/bus is not root!
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


So what should I do? I am currently completely unable to do anything with my dvd drive, so should I just try to write to the dvd using a program through Wine?

---

### Post by SuperFreak on 2013-08-03
Not quite sure which DVD program you are using to write DVDs but I have found [K3B]("https://help.ubuntu.com/community/K3b") the most reliable and has pretty consistent results. I am not able to comment on the output in your post I am afraid, perhaps someone better able will help

---

### Post by zteam2 on 2013-08-04
You should first of all tell us what DVD-burning software you are using.

Also it might be helpful to post the model of your DVD-burner just in case.

---

### Post by ibjsb4 on 2013-08-04
Really shouldn't need to mess with proc settings.  As mention, k3b may be a better choice for you.

```
sudo apt-get install k3b
```

---

### Post by 4Foot on 2013-08-04
I wrote about this issue in another thread but it seems to be going nowhere so please let me chip in. I was using Mint 15 quite happily on my Linux box and about three weeks ago, (early July) lost the ability to write anything to a DVD using my Plextor burner. I used K3b primarily but have tried Brasero and Xfburn as well with no better result. Error messages vary but almost always the SW starts to work but fails in calibration or very early on in the process. The DVD media is then ejected. Nothing has been written to the DVD and I can and have used the ejected DVD's in another burner on my Mac. 

I switched to Ubu 13.04 in hopes of clearer skies but no joy. Same problem. I did find a thread which recommended switching from the stock wodim to cdrecord and mkisofs which I did on my Mint box to no avail. Tried that on Ubu but it would not let me update saying that I was trying to install an older version of the software. It will not burn iso images or data. Nada

If I had not seen this issue reported in a few other places I would be thinking that my Plextor was pooched but it does not appear to be just me. I will however swap out my drive later this week and report back if that is the problem. I do not have much confidence in that as a problem however, that Plextor is as solid a drive as I have ever owned. I would be very grateful for a Software fix. 

Cheers

4Foot

---

### Post by 4Foot on 2013-08-04
Update:

I have no patience! So, I have an external USB Lightscribe DVD Burner and on a whim I hooked it up to my Linux box and it is currently just humming along burning an ISO using K3b. I still cannot verify that there is not an issue with an internal drive and how Ubu sees those drives but I have a second internal which I will install and test. I will report back but, preliminarily, I am fairly certain that my problem is that my Plextor is either not recognized by this latest version of kernel or that it is borked. 

I loved this Plextor, hate to see this. 

Happy Trails

4Foot

---

### Post by chambogorden on 2013-08-07
Hey everybody sorry for late reply, been busy lately. I already tried k3b(that and xfburn were my first choices) found a thread over at winetricks that suggested a possible work around, but it also stated it required modifiying the Linux kernel, which I would rather avoid. I was able to write to the disc on my other laptop(a Toshiba) on an unupdated version of Ubuntu 13.04, so it is not something with Ubuntu itself, my guess would be one or more of the updates(had an issue with the kernel header due to a faulty update recently and only got it mfixed yesterday), so I am able to write to discs, just not on this laptop. And @4foot, yeah I'm thinking about doing a dual boot with either crashbang/slackware as Ubuntu proves invaluable for some of what I need to do(mostly just things involving guis) but I prefer other distros for things like development or server building(which is mostly just personal preference really, I know this issue is solveable, but it requires rather lengthy methods to do so, some of which would require no end of compiling, so I'll just try out various Linux distros and go from there). And one more thing, on this laptop(Dell Latitude E6400) I am able to completely remove the dvd drive and hook it up to another comp running Fedora and the drive writes fine, so its something with part of a fully updated Ubuntu(or maybe just a program that grabbed hold of the drive and doesn't show up :/).

---

### Post by 4Foot on 2013-08-07
Thanks for the update Chambogorden, I wish you luck and agree that it may be a kernel issue since it is cross platform. I swapped out my Plextor for a Sony I had laying around and I can now burn again so colour me solved. Not sure if my Plextor is pooched or not but will keep it around for a slow day project. 

Good luck C.

4Foot

---

### Post by mcotoole2 on 2013-10-01
I had the same problem with multisession discs on when I upgraded to 12.04; neither K3B nor Brasero worked.  I installed the terminal application cdw and it handles multisession without a problem.

---

