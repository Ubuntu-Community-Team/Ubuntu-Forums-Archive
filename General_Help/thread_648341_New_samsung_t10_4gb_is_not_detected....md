---
title: "New samsung t10 4gb is not detected..."
date: 2007-12-23
forum: General Help
---

### Post by Virgilio on 2007-12-23
I heard that the samsung t10 wont work with linux because of the mtp drivers but i know that some people got it to work. Can anyone please tell me how? im running Gutsy if that helps. and this the link for the mp3 player [http://www.anythingbutipod.com/archives/2007/10/samsung-ypt10-review.php]("http://www.anythingbutipod.com/archives/2007/10/samsung-ypt10-review.php")

---

### Post by fernandez.garza on 2007-12-24
yes, i am having the same problem with linux, please help me.

Thanks in advanse

---

### Post by Tollkirk on 2008-01-01
I can successfully transfer files to the T10 using the command line "mtp-connect --sendfile" (having installed libmtp_0.2.4), but I can't figure out how to make Amarok or Rythmbox see the device. Any ideas anyone?

---

### Post by mcallenSchmee on 2008-01-04
I've been looking into the samsung players, and it seems like most of them can be used like usb mass storage, but you may have to upgrade the right firmware.

---

### Post by yahoo on 2008-03-01
Hi all.
I have just finished flashing mu YPT-10 as described on pages starting here:
[http://www.anythingbutipod.com/forum/showthread.php?t=21463](http://www.anythingbutipod.com/forum/showthread.php?t=21463)

I did this in WindowsXP though!!!

Read these posts:

Robind post # 46 page 3 has one download required of his hand-edited version of the firmware MSC v1.55 for T10.

fde post #71 page 4 for download of Korean firmware discussed all through the thread.

Amprous post #120 page 6 has the summary I followed.

It was all successful, just as Ambrous described - except he didn't mention to disconnect it after all files have been transferred in step 8, before turning it on (and again and again).

My Samsung YPT-10 nowmounts automatically, if a little slowly, in my Gutsy system.
It does not show up as a removable media in Rhythmbox like my Sansa E260 does, so I'll have to work on that :P.

A nice player, with excellent FM radio for here in New Zealand.

Cheers
Yahoo

---

### Post by Headly B on 2008-04-29
Hi,

Changing the firmware is really not necessary to get your T10 t work in Ubuntu, and it seems to be a nice way of bricking your device. The reason to change the firmware is to change it from a MTP device to a UMS device. This allows you to use it as a mass storage device, so you can drag and drop content from your computer to your T10. However using libmtp and mtpfs will give you the same functionality.

Solutions for using the T10 with Ubuntu are discussed at length here:
[http://ubuntuforums.org/showthread.php?t=651894](http://ubuntuforums.org/showthread.php?t=651894)

Things have got considerably more straight forward since the release of the Hardy Heron, because in 8.04 the libmtp and mtpfs packages are already installed. The first message in the link above is mainly concerned with getting these packages installed in Ubuntu 7.10; this may not be as difficult as it looks but when you're completely new to Linux (as I am) it was enough to confuse me and put me off trying. Users of Ubuntu 8.04 can skip all of that.

libmtp allows the computer to recognise your MTP device and mtpfs  
allows you to mount it like an external drive. Then you can simply drag and drop files directly onto your T10. I ran into one problem using mtpfs that's worth noting...  

To mount the T10 properly you need to go: system\administration\users and groups\manage groups. Make sure your user is ticked as a user in the "fuse" group. _Then restart Ubuntu_. If this doesn't work (I think it should but I  
tried both of these things before realising that I needed to reboot to get things working) in a terminal write "sudo usermod -a -G fuse <yourname>". Again you may need to restart Ubuntu to get things working.

I think that getting Amarok or any other media players to recognise your T10 involves using a specially compiled version of
that player...that gets way beyond my simple grasp of things. Besides, I like to just drag and drop my music onto my T10 without the help of any other software.

Finally, the SVI conversion tips in the link at the start of this  post are great! Very simple to do and works 100%. 

Best of luck,

Headly B

---

