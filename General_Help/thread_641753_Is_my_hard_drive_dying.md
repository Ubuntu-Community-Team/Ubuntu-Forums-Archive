---
title: "Is my hard drive dying?"
date: 2007-12-15
forum: General Help
---

### Post by amunimanghi on 2007-12-15
Hi,

Today I was in windows and was playing a game. I paused it and went to help my little sister with something. I came back after about an hour and a half later and the computer was in Ubuntu. What amazes me is that I have the bios set to automatically boot up the windows hard drive. I thought something stupid may have occured and went on. I reset the first hard disk that boots up to the windows one and resumed my game. About 5 minutes into the game, the entire computer freezed and I heard clicking noises/sounds. I got worried and manually shutdown the computer seeing as there was no other way. I came back an hour later wanting to type up an essay and the computer wouldn't start. It woudl freeze at my bios splash screen while the hard drive would 'turn off and turn on'. By that I mean I would hear it spin, and then stop spinning. Eventually, (after 5-10 minutes), I got passed the bios screen and loaded up ubuntu. Fsck ran on my windows hard drive which spit out an error. I logged in and went to /var/log/fsck/checkroot. This error was located inside of it: ```
Log of fsck -C -a -t ext3 /dev/sda1 
Sat Dec 15 17:19:53 2007

fsck 1.40.2 (12-Jul-2007)
/dev/sda1 was not cleanly unmounted, check forced.
/dev/sda1: 137171/9371648 files (1.3% non-contiguous), 11407725/18729774 blocks
fsck died with exit status 1

Sat Dec 15 17:22:24 2007
----------------
```

Does this mean my hard drive is dying/dead? If so, can I still mount it so I can backup. Thanks in advanced.
~Amunimanghi

---

### Post by Eddie Wilson on 2007-12-15
By the noise that you heard coming from your hard drive It could very well be going bad. Most of the time when the hd makes clicking noises its done for. You need to get the data off of if soon. Very soon, if not already, you will not be able to access any data at all. 
Eddie

---

### Post by Sef on 2007-12-15
First I would definitely pull off any information that you need off your hard drive asap.  I use Knoppix to do that; however, you could try with Ubuntu.  It could work too.

Second, the clicking could indicate a bad hard drive, but that usually happens over a period of time.  More likely, your software has gotten messed up.  

Third, using Ubuntu Live CD, run an fdisk check.  See if that will fix the problem.

---

### Post by amunimanghi on 2007-12-15
I believe my data is lost as well. I can no longer find /dev/sdb1 in the /dev folder. I'll try the live cd and see if I can still salvage the documents at least. Thank you for your help.

---

### Post by Sef on 2007-12-16
If you really need the data, then you can take it to a recovery center.

---

### Post by joeyteetops on 2007-12-21
> the entire computer freezed and I heard clicking noises/sounds. 
Your drive likely has a bad magnetic head stack.  When the read-heads cannot see servos they start banging stupidly instead of hovering over the tracks when they operate properly.   Drives in the situation will deteriorate rapidly and it's important not to jack around with them if the data on there is important to you as that can lead to the heads crashing into the platters if they haven't already.    

If you are serious about needing professional recovery there's some good places out there.  Be sure to find a place that'll give a free evaluation (there are plenty) and give you a decent price quote over the phone (as some places will give you price ranges like 200 to 3000 dollars).  I'd personally recommend [gillware data recovery]("http://www.gillware.com") in your situation, they'll typically charge about 500 bucks for your situation I think.  Otherwise ontrack or actionfront can be very good as well (my company has used all 3). 

Best of luck.

---

### Post by az on 2007-12-21
Stop using the computer immediately.

Using another computer, burn a copy of the ubuntu-rescue-remix and boot it.  You will need another drive onto which to copy the data from your failing drive.  Use gddescue to image your drive.

If you can't use the filesystem from the image, you can pull files from it using file-carving.

see:
[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

---

