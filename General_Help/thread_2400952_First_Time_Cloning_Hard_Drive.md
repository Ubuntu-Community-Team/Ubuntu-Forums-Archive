---
title: "First Time Cloning Hard Drive"
date: 2018-09-12
forum: General Help
---

### Post by Majik_420 on 2018-09-12
so I have a dual boot older HP from around 2008 and I'm upgrading the HD to a 2TB just to keep it going a bit longer while I build my first setup from the case on. I am a novice with computers and troubleshooting, I can search and generally figure out what I need to but I find this forum to be immensely helpful in addition to my limited time available for researching problems at the moment.

I'm hoping I can also incorporate this cloned HD to my new setup after its finished, specifically so I can keep Adobe CS5, but I read something in passing about switching motherboards possibly causing a problem for programs/licensed software like that. any tips there appreciated.

So I got everything hooked up and a few partitions cloned over with no problem using Macrium Reflect. I tried to do them all at once, but got errors. So I tried them individually and narrowed it down to 2 partitions with 2 separate errors. Now i'm thinking about scrapping the macrium clone and trying clonezilla.

I don't even know if I need all these partitions setup the way it is, so maybe its a good time to clean that up as well? 
it seems like its slightly excessive; I only use the Windows 7 partition for CS5 and browsing if I'm already logged in. I generally prefer to use my Kubunutu partition for general browsing and I have a movie collection that I think I somehow lost access to a while back. Also I think currently Kubunutu partition will not boot. I keep meaning to dig in, but pretty busy with work currently. I have more time in the winter for computer issues.

So right now the new HD wont boot. I dont know if I need to install a bootloader or if that is supposed to copy over from partition 1 or what. 

I had my wisdom teeth out this morning also so I'm just trying to be productive while I'm home but I'm getting pretty close to wanting to just lay down for a bit.

Ill be searching in the mean time... thanks.

---

### Post by HermanAB on 2018-09-12
You don't actually need any special tools to clone a disk.

To clone a disk both the source and the destination must be unmounted and not in use.  To achieve that, boot from a Linux install medium.  Then, look at /dev to see the device names of the two disks.  (Plug in the source disk and run 'ls /dev' - it may already be plugged in if it is internal.  Plug in the destination disk and run 'ls /dev' again). 

Once you have the device names, e.g. /dev/sda and /dev/sdb and know for sure which is which, you can copy the disk with 'cat', e.g.:
# cat /dev/sda > /dev/sdb

La voila.

---

