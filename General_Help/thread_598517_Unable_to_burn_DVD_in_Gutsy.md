---
title: "Unable to burn DVD in Gutsy"
date: 2007-10-31
forum: General Help
---

### Post by jjfire on 2007-10-31
I t doesnt matter what program I use I am unable to burn anything the program will load and seems to start burning but the progress indicator doesnt move at all. I have tried both brasero and k3b. It worked fine in 7.04 i upgraded to gutsy and now it wont work, any ideas ??

---

### Post by jjfire on 2007-11-01
Well here is an update to my dilemna, I was able to burn a music cd last night, so it seems I have narrowed my problem down to data dvd's.  I really need some help with this guys.

---

### Post by JavierRio on 2007-11-02
The same with me.

---

### Post by junjan on 2007-11-03
I had the same problem since Ubuntu Feisty, CD burning was fine, but DVD won't work. It began but stopped with error , ruining the DVD in the process.  I tried all the burning software around, gnomebaker, brasero, k3b, etc. I also tried many solutions coming from different forums, tested different kernels, change unit names and aliases, go through user-permissions discussions... No way. Finally I gave up and kept using Windows for DVD burning until I discovered that Nero software existed for Linux. I installed version 3.0.0 waiting for a different error screen and suddenly it worked! Full recovery like in Dapper Drake times,
Give it a try if you have the same problem.

---

### Post by JavierRio on 2007-11-14
I installed Nero but it doesn't work. It happens the same than with the others programs to burn dvd in that i tried in Gutsy (Gnomebaker, K3b), simulates but doesn't burn, says that burning process is starting but stays in that stage and you lose control of the system and have to reset.

---

### Post by wingrider101 on 2007-11-18
I have very similar problems to the ones earlier.  Using Ubuntu Gutsy Gibbon 7.10, and with Braser, K3b, Gnomebaker, DeVeDe (I've tried them all!)  I am unable to burn a DVD+R or DVD-R video or data to completion.  The following happens:

1.  Execute the burning program, all goes well.
2.  Insert the blank DVD+R (or -R), and the burn starts
3.  On all of these programs the counter or indicator immediately goes to 100% (complete)
4.  On all of these programs the program then says "Closing Disk"
5.  On all of these programs the disk ejects
6.  The DVD obviously did not burn to completion and the DVD blank is now ruined

It's getting really expensive to test this over and over again with no luck.  Can one of the "Pros from Dover" step in here and give us a hand?  I am not new to Linux, but I don't know what to try next.  All of the programs have all of their requisites matched.  All of them run.  The logs are all gibberish to me, and need someone who really knows what they are doing to look at them and tell me what to try.

Help me Obi  Wan Kenobi... You're my only hope!!

:confused:

---

### Post by GreenMeanie on 2007-11-19
I keep getting media is not formatted or unsupported errors when trying to burn dvds?
It is quite annoying anyone figure this problem out yet?

---

### Post by dexter on 2007-11-21
I've also faced this problem in Gutsy, after some experimenting I found how to get it working. I use GnomeBaker as a always have, when clicking burn, switch to the tab filesystem in the dialogue that appears and make sure only Joliet is checked.

---

### Post by NightCrawler03X on 2007-12-04
This happened for me too.

Then I remembered that ubuntu automounts cd/dvd.
You need raw access, that is, they can't be mounted.

If, for example, you have a dvd in a dvd-rom drive, and a blank dvd in a dvdrw drive, unmount the two drives:

Go to your terminal
```
umount /dev/scd0
umount /dev/scd1
```
The "/dev/scd0" and "/dev/scd1" might be different for you (that is, you have a different file controlling your drives.

Most, if not all, cd/dvd authoring software on linux requires RAW access the any drive your using, so you *must* unmount the drives you wish to use, first.

Regards

---

