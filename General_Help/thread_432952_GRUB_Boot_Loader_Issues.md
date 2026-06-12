---
title: "GRUB Boot Loader Issues"
date: 2007-05-04
forum: General Help
---

### Post by Forcepath on 2007-05-04
Does anyone have knowledge of GRUB boot loader?

My problem: everytime I try to boot, I get Error 22: Partition not found. But this is the weird part, I know that partition is there, because I have a separate GRUB program (Super Grub Boot I think it's called), and when I use that grub to boot to Linux (from a CD), it works just fine.

Here's my grub boot list (the important part):

```

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9c2953fb-2611-4826-9620-d7766b03374b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9c2953fb-2611-4826-9620-d7766b03374b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```


As an aside I've used the GRUB command line to successfuly
```

root (hd1,0)

```
however I get the NTLDR error when I try to boot.

I have two hard drives, one IDE and one SATA.  I've been dual booting Ubuntu and Linux off my SATA drive, but after changing from Feisty amd64 to 32bit, I've been having the above issue.

My drive map looks like this:
```

(hd0)	/dev/hdd
(hd1)	/dev/sda

```

So what I THINK my problem is: when I initially boot my computer to my SATA hard drive, GRUB doesn't recognize my SATA drive. Any ideas on how to fix this? 

Currently I'm booting by having wiped my MBR clean and using the windows boot, and when I want to boot to Ubuntu I use the GRUB off of a CD and navigate through a few windows. Tedious? Yes. Annoying? Yes. Functional? Well, you decide. 

Thanks for reading this post, and I hope to maybe find some answers here today, I've been scouring Google/Ubuntu forums but there just isn't an end in sight for me quite yet.  Hopefully someone more knowledgable than I can help me out here!  :D

---

### Post by m.musashi on 2007-05-04
If I had a nickel for every GRUB question...

Maybe someday they will have a very nice, clean graphical boot tool. In the meantime, try [this thread](http://ubuntuforums.org/showthread.php?p=121355). If that is similar to what you already did, you can look [here](https://help.ubuntu.com/community/GrubHowto) for some more info on GRUB. Perhaps something there will get you moving in the right direction.

---

### Post by Forcepath on 2007-05-04
> **m.musashi said:**
> If I had a nickel for every GRUB question...

Maybe someday they will have a very nice, clean graphical boot tool. In the meantime, try [this thread](http://ubuntuforums.org/showthread.php?p=121355). If that is similar to what you already did, you can look [here](https://help.ubuntu.com/community/GrubHowto) for some more info on GRUB. Perhaps something there will get you moving in the right direction.

Appreciate it, I'll give it a shot at least :)  Thanks for the advice!

How many nickels would you have?  ;)

---

### Post by m.musashi on 2007-05-04
> **Forcepath said:**
> How many nickels would you have?  ;)
Well, probably only 20 or 30 so far, but in time I'm sure I'd get several dollars worth :).

---

### Post by Forcepath on 2007-05-04
I'll be sure to post many many more GRUB questions, hopefully someone will start giving you nickels someday!

---

### Post by m.musashi on 2007-05-04
Hey, one more thought. What if you set up GRUB on the IDE drive and you boot that drive (or vice versa)?

EDIT: you haven't changed partitions lately have you? Or changed the drive order in the BIOS? That will usually make GRUB stop working. Was it working before and then stopped or it just never worked?

---

### Post by m.musashi on 2007-05-04
Okay, just thought of something else too. I noticed that you have HD1 in the GRUB menu for root but the boot drive will be HD0. That's isn't necessarily a problem but if things aren't set up right it will be looking in the wrong place for the boot files.

I'm off to a meeting, but I will check back with you later. Hopefully you will have some luck with all this.

---

### Post by Forcepath on 2007-05-04
No, I have never had grub working with Ubuntu off of my SATA drive with Windows as my first install.  

I'm wondering about your latest suggestion though, GRUB boots off of hd1 (so I think, anyway I could check that?).  So since GRUB is booting off of HD1, why can it not recognize the ext3 partition of linux (hd1,6)?

The only partition change was that I previously used hd1,6 as an amd64 version of ubuntu, however I formatted that and installed feisty over it.  

I will take a look at installing GRUB on hd0 and having it boot hd1, I'm not sure how exactly to do that, but I'm willing to poke around the internets!  THanks again for your advice, I will continue working on this!

EDIT: Just saw the end of your post, I'll go ahead and do some Googling, and let you know what I come up with.  I'll check back here in about an hour or two to see if you've come up with anything and post my results as well!

---

### Post by confused57 on 2007-05-04
If you decide to install grub to your IDE drive (hd0), you can use the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by m.musashi on 2007-05-04
If you boot HD1 by changing it in the BIOS then it will become HD0 and the files it is looking for on sdb will now be on sda. We can fix it, but we have to first get the GRUB menu to load.

---

### Post by Forcepath on 2007-05-04
I think I may have accidentally mislead you.  The GRUB loads just fine right now, but when I select an OS to boot from, I get the Error 22: Partition not found error, even though I'm typing to you from that partition right now.  

To boot to Ubuntu at the moment I have a CD with GRUB on it, which loads the OS with no issues.

---

### Post by mikewhatever on 2007-05-04
I was wondering what does the device map has to say. Can you post the output of this:
> cat /boot/grub/device.map/boot/grub/device.map

Here's why I think it's relevant [http://users.bigpond.net.au/hermanzone/p15.htm#device.map](http://users.bigpond.net.au/hermanzone/p15.htm#device.map)

---

### Post by m.musashi on 2007-05-04
Okay, good. If you have grub loading then we have less work.

I'm not sure, but I'm thinking the problem has something to do with partitions not matching. Can you post the output of
```
sudo fdkik -l
```

I'm working on a couple grub problems so I hope I'm not getting confused.

---

### Post by Forcepath on 2007-05-04
> **mikewhatever said:**
> I was wondering what does the device map has to say. Can you post the output of this:
/boot/grub/device.map

Here's why I think it's relevant [http://users.bigpond.net.au/hermanzone/p15.htm#device.map](http://users.bigpond.net.au/hermanzone/p15.htm#device.map)

I posted the output in my original post, but here it is again for you :)

```

(hd0)   /dev/hdd
(hd1)   /dev/sda

```

---

### Post by Forcepath on 2007-05-04
> **m.musashi said:**
> Okay, good. If you have grub loading then we have less work.

I'm not sure, but I'm thinking the problem has something to do with partitions not matching. Can you post the output of
```
sudo fdkik -l
```

I'm working on a couple grub problems so I hope I'm not getting confused.

Was that a typo?  Heh I get

```

sudo: fdkik: command not found

```

Am I missing a dependency you're looking for?  :)

---

### Post by confused57 on 2007-05-04
The command is:
```
sudo fdisk -l
```
the -l is a small "L"

I suppose reinstalling grub to (hd0), using the live cd, didn't work.

---

### Post by Forcepath on 2007-05-04
No reinstalling the GRUB from the Live CD didn't work for me.  Still getting the same Error 22. 

Here's the printout of fdisk:

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       38913   178361662+   f  W95 Ext'd (LBA)
/dev/sda5           16709       29859   105635376    7  HPFS/NTFS
/dev/sda6           29860       30234     3012156   82  Linux swap / Solaris
/dev/sda7           30235       38913    69714036   83  Linux

Disk /dev/hdd: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       14945   120045681    7  HPFS/NTFS

```

---

### Post by confused57 on 2007-05-04
I'm not sure what the problem might be, here's some possible solutions for error 22:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22)

What does the Super Grub Disk show as your root partition when you boot from SGD?

---

### Post by m.musashi on 2007-05-04
> **Forcepath said:**
> Was that a typo?  Heh I get

```

sudo: fdkik: command not found

```

Am I missing a dependency you're looking for?  :)

Sorry about that. Yes, a typo. Thanks confused but I think that name applies to me right now :).

Okay. I may be barking up a wrong tree but your boot files are on (hd1,6) but your fdisk says they are on sda7. Generally sda7 would translate as (HD0,6) but having one SATA and one IDE might screw up that assumption, I don't know. So, try this. Reboot and then highlight the line for booting Feisty and press the letter e. This will show you the contents of the menu for that boot option. It should look like
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9c2953fb-2611-4826-9620-d7766b03374b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```
which I just copied from your menu.lst that you posted, and change it to look like
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd**0**,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=**/dev/sda7** ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```
This will not be a permanent change so no worries if it doesn't work. I am also making the assumption that grub is loaded on on the sda disk. You might have said this already but I don't remember.

I also changed the UUID because there is no way of knowing what that actually is. This is much easier to debug.

EDIT: oops, after making those changes press enter and then press the b to boot it.

---

### Post by m.musashi on 2007-05-04
If that doesn't work, I have another idea. Which drive do you want to be the MAIN drive (i.e. the one the computer will first try to boot from)? I think you have that set as the IDE drive. Let me make a suggestion that will be somewhat roundabout but should get things working right. As it is, I'm kind of confused as to which drive is which and where grub is and so on.

If you haven't already, make sure your important files are backed up somewhere. None of this should damage anything but you never know.

We need to make sure your drives aren't changing as that will really get us confused. Lets set the SATA drive  to be the main one. Use your BIOS to make it the first drive.

Boot a live CD and then do the grub set up in one of the earlier posts. It starts by having you type grub in a terminal and then finding /boot/grub/stage1.

I'm hoping that will result in everything being set on the MBR of the SATA drive. If all goes well, that should fix it.

It's possible that you will need to mount the drive before the steps above will will work. We might also need to tweak the menu.lst but we can cross that bridge later.

---

### Post by Forcepath on 2007-05-04
Wow, hey that worked!  Booted no problem.  I'm assuming then I just need to go change my menu.lst file from 1's to 0's?!??!??!  


(This is one very excited dude!)  Hmm.  However, now Ubuntu doesn't boot at all, and my keyboard keys (capslock and scroll lock are flashing on and off...)

---

### Post by confused57 on 2007-05-04
> **m.musashi said:**
> Sorry about that. Yes, a typo. Thanks confused but I think that name applies to me right now :).

Okay. I may be barking up a wrong tree but your boot files are on (hd1,6) but your fdisk says they are on sda7. Generally sda7 would translate as (HD0,6). So, try this. Reboot and then highlight the line for booting Feisty and press the letter e. This will show you the contents of the menu for that boot option. It should look like
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9c2953fb-2611-4826-9620-d7766b03374b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```
which I just copied from your menu.lst that you posted, and change it to look like
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd**0**,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=**/dev/sda7** ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```
This will not be a permanent change so no worries if it doesn't work. I am also making the assumption that grub is loaded on on the sda disk. You might have said this already but I don't remember.

I also changed the UUID because there is no way of knowing what that actually is. This is much easier to debug.

EDIT: oops, after making those changes press enter and then press the b to boot it.

I knew it was just a typo on your part, I definitely make my share of them.  Good point about the UUID's possibly being wrong.

---

### Post by Forcepath on 2007-05-04
Okay well it boots when I change hd1 to hd0, however when I changed the UUID to root=/dev/sda7 Ubuntu froze on the loading screen.  

Going to try again and see if perhaps I mistyped something on my end.

---

### Post by m.musashi on 2007-05-04
> **Forcepath said:**
> Wow, hey that worked!  Booted no problem.  I'm assuming then I just need to go change my menu.lst file from 1's to 0's?!??!??!  


(This is one very excited dude!)  Hmm.  However, now Ubuntu doesn't boot at all, and my keyboard keys (capslock and scroll lock are flashing on and off...)

Which one worked? And if ubuntu doesn't boot does that mean it's not fixed or that there is a new problem?

---

### Post by Forcepath on 2007-05-04
My apologies, it was a typo and a misunderstanding on my end.

I didn't realize you didn't want me to change the UUID to the /dev/sda7 on the GRUB command line.  You meant to do that only on menu.lst.  I also typed it into the GRUB command line the first time, hence the startup error.

It all works perfectly now :)

---

### Post by m.musashi on 2007-05-04
REALLY? Great because I was starting to get lost. Would you say this is now resolved or do we still need to tweak a few things to make it permanent? Or are you comfortable doing that?

---

### Post by Forcepath on 2007-05-04
I was lost too, but that seems to have fixed it!  

Definitely resolved, if there are any other issues, they aren't related to bootup!  :)  

Once again, your help was invaluble, thank you!

---

### Post by m.musashi on 2007-05-04
No worries. Glad I was able to help (it happens so rarely:)).

You might want to edit your fist post and check the "resolved" box. It won't close the thread (I don't think) but it lets people know it's both resolved and contains a solution that worked for someone. If you have new issues I'd start a new thread so someone with that experience can find it (hopefully).

---

