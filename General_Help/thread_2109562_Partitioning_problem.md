---
title: "Partitioning problem"
date: 2013-01-27
forum: General Help
---

### Post by ZoCo on 2013-01-27
I saw posts on similar problems but not my exact problem and I don't want to apply someone else's instructions and muck it up more
 My windows os became unusable and I was running low on space in Ubuntu (12.04) 
I did a search and found a thread telling me to delete the windows partition and move the slider to reclaim the space, so I booted the live CD, opened gparted, deleted windows partition then  the slider wouldn't go that way, I ended up formatting the free space so it was the same as Ubuntu's then copied my Ubuntu partition into this 120 gigs of space told it to boot that partition 
rebooted it loaded fine everything looked great, In the instructions I read it said to go  to terminal do "sudo update-grub" command, did that, restarted, it reverted back to booting the original copy of ubuntu, now it says there is only 4 gigs of free space in  the 120g section and 4gigs free space in the original partition ( that's what is was before ) idk what the heck I did but I can't begin to figure out where to go from here
I felt totally confident adjusting the partition when I read the instructions, now I feel like a total noob :confused:

---

### Post by ibjsb4 on 2013-01-27
How bout posting a pic of gparted, let us see what it looks like.  Or do it in terminal, enter:

```
df
```

---

### Post by ZoCo on 2013-01-27
Thought I forgot something ... sorry
 sda2 is the copy of sda5

---

### Post by ibjsb4 on 2013-01-27
Well, I really don't how you pulled that off either :)

sda5 is the orginal and sda2 is the copy, so how bout this.

Go back to plan "A" and extend sda5.  Do that with gparted on your live CD and ..

#1 Delete sda2 and do not format it, just leave it as free space.

#2 Right click on sda3 and use the resize option and resize to take up the 116.99G that use to be sda2.  Then ..

#3 Resize sda5 to take up the new free space that will appear after you complete step #2.

This is going to take some time to complete.  

Any questions?  Please post back before you start with any :)

Also your computer may not boot after this operation is completed.  If this happens, do not panic, grub can be repaired afterward if needed.

---

### Post by Bucky Ball on 2013-01-28
Boot into the install on sda2 and:
```

sudo grub-install /dev/sda
```... if what you're wanting is for that install to be running the show. Once it's there:

```
sudo update-grub
```

... will pick up any and all OSs on your machine. If you are not getting a menu of OSs at boot then hit shift after the BIOS screen. I'm presuming you are not and the machine is booting into the wrong install by default?

---

### Post by ibjsb4 on 2013-01-28
@Bucky Ball

If I understand correctly his 16G (sda5) orginal turned into 112G (sda2) copy for no good reason.

---

### Post by ZoCo on 2013-01-28
> **ibjsb4 said:**
> Well, I really don't how you pulled that off either :)

sda5 is the orginal and sda2 is the copy, so how bout this.

Go back to plan "A" and extend sda5.  Do that with gparted on your live CD and ..

#1 Delete sda2 and do not format it, just leave it as free space.

#2 Right click on sda3 and use the resize option and resize to take up the 116.99G that use to be sda2.  Then ..

#3 Resize sda5 to take up the new free space that will appear after you complete step #2.

This is going to take some time to complete.  

Any questions?  Please post back before you start with any :)

Also your computer may not boot after this operation is completed.  If this happens, do not panic, grub can be repaired afterward if needed.

Ok sounds simple enough, I went into livecd, gparted, deleted sda2..... now sda 3 isn't showing on the partition table then when i right click and click information it tells me this "Busy (At least one logical partition is mounted)"
lol now what?
 I am still in the livecd lol Thought I better stay put till I found out what to do next

---

### Post by furything on 2013-01-28
Is this not to do with drive signature (uuid) and ftsab.
Sda5 will be written to fstab so even if grub is reading sda2 the ftsab will tell it to mount up sda5.

You need to get the uuid of sda2 and change the fstab on sda2 to look at it's self

[http://linuxconfig.org/how-to-retrieve-and-change-partitions-universally-unique-identifier-uuid-on-linux](http://linuxconfig.org/how-to-retrieve-and-change-partitions-universally-unique-identifier-uuid-on-linux)

If grub is pointing at sda2 (look in grub.cfg) then a reboot on changing the fstab (on sda2) should cause it to boot to sda2. You can then get rid of sd5 (if you like)

---

### Post by ZoCo on 2013-01-28
> **furything said:**
> Is this not to do with drive signature (uuid) and ftsab.
Sda5 will be written to fstab so even if grub is reading sda2 the ftsab will tell it to mount up sda5.

You need to get the uuid of sda2 and change the fstab on sda2 to look at it's self

[http://linuxconfig.org/how-to-retrieve-and-change-partitions-universally-unique-identifier-uuid-on-linux](http://linuxconfig.org/how-to-retrieve-and-change-partitions-universally-unique-identifier-uuid-on-linux)

If grub is pointing at sda2 (look in grub.cfg) then a reboot on changing the fstab (on sda2) should cause it to boot to sda2. You can then get rid of sd5 (if you like)

I have already started ibjsb4's instructions .... sda2 is now gone

---

### Post by furything on 2013-01-28
> I have already started ibjsb4's instructions .... sda2 is now gone

Ok but bear in mind the uuid stuff for the future it may save you a lot of headaches. I did something like this when moving from LVM to Tb drive. Had to play with uuid in order to get my swap file partition alive as well as main partition.

It kept warning me that drives were missing because it kept looking with the now absent LVM

---

### Post by dino99 on 2013-01-28
a few questions:

- do the PQSERVICE partition still needed ? (/dev/sda1) . If not , then format it.

- when formatting: set no more than 3  "primary" partitions, better to set a huge "extended" one, then inside it you can set other partitions . 

- for a standard installation, set:
use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode (Something Else installer choice).
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by ibjsb4 on 2013-01-28
> when i right click and click information it tells me this "Busy (At least one logical partition is mounted)Using the live CD you should not have mounted anything, but you did.  So just use gparted to unmount sda5 and if needed sda3.  Then you should be ok.

Note: may also be necessary to turn off swap (sda6) with gparted.

EDIT:

> It kept warning me that drives were missing because it kept looking with the now absent LVM

I did no know this was LVM and I do not know what effect this has.

---

### Post by ZoCo on 2013-01-28
> **dino99 said:**
> a few questions:

- do the PQSERVICE partition still needed ? (/dev/sda1) . If not , then format it.

- when formatting: set no more than 3  "primary" partitions, better to set a huge "extended" one, then inside it you can set other partitions . 

- for a standard installation, set:
use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode (Something Else installer choice).
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)


I'm not sure if I need PQSERVICE, I don't know what it is, I'm guessing it is  Windows recovery but I am not sure
If I can get ibjbs4's method to work for me I will be down to 3 partitions with a sub-partition inside the 3rd ( I think)
your instructions are greatly appreciated dino99 but to be honest  a bit over my head

I don't understand why it's telling me dev/sda 3 is in use  (see earlier attachment) and therefore can't be altered while I'm running Ubuntu from the live cd , I'm stuck at this point and don't know where to go from here, I hate being such a dunce  but If i knew all this stuff I wouldn't need the help would I ? :lolflag:

---

### Post by ZoCo on 2013-01-28
> **ibjsb4 said:**
> Using the live CD you should not have mounted anything, but you did.  So just use gparted to unmount sda5 and if needed sda3.  Then you should be ok.

Note: may also be necessary to turn off swap (sda6) with gparted.

EDIT:



I did no know this was LVM and I do not know what effect this has. 


THANK YOU ibjsb4 !! i needed to turn swap off and it allowed me to move sda3
I'm gonna apply it and see if it boots
hopefully I will be back sooner rather than later ):P

I don't know what LVM is XD

---

### Post by dino99 on 2013-01-28
when you see a "key" inside gparted screen (on the line referring to a partition), its meaning that this partition is mounted, and so cant be tweated.

If you shutdown your system, then make a cold boot on the livecd, none partition is mounted (logical) when you select the hdd inside gparted (right top corner)

---

### Post by ZoCo on 2013-01-28
> **dino99 said:**
> when you see a "key" inside gparted screen (on the line referring to a partition), its meaning that this partition is mounted, and so cant be tweated.

If you shutdown your system, then make a cold boot on the livecd, none partition is mounted (logical) when you select the hdd inside gparted (right top corner)

the swap file was on and that was why I couldn't adjust sda3 and therefore 5 i turned it off as per earler instructions and that has worked getting ready to apply and reboot now

---

### Post by ZoCo on 2013-01-28
> **ibjsb4 said:**
> Using the live CD you should not have mounted anything, but you did.  So just use gparted to unmount sda5 and if needed sda3.  Then you should be ok.

Note: may also be necessary to turn off swap (sda6) with gparted.

EDIT:



I did no know this was LVM and I do not know what effect this has.

worked fine .... when I got the boot screen I chose the first linux entry at the top, as always, and it booted right away \\:D/

thank you ibjsb4 you saved a very confused lady :D
only 2 questions now
do I need to turn swap back on? , I would imagine yes and ....
do I use sudo update-grub to clean up the boot screen and get rid of all the extra entry's that the  growing sda2 made ?

---

### Post by ibjsb4 on 2013-01-28
Your welcome :) glad it all worked out for you.

Yes, turn swap back on.

You can update grub and see if it does anything.  Afterward if you still have a bunch of grub entries; lets have a look.

Open a terminal and enter:

```
l /boot
```

That's a small L /boot

---

### Post by ZoCo on 2013-01-28
> **ibjsb4 said:**
> Your welcome :) glad it all worked out for you.

Yes, turn swap back on.

You can update grub and see if it does anything.  Afterward if you still have a bunch of grub entries; lets have a look.

Open a terminal and enter:

```
l /boot
```

That's a small L /boot

yeah it showed me in terminal and it was all still there so i used> l /boot
and it showed me this .... (see attachment)

---

### Post by oldfred on 2013-01-28
Looks like it may be time to do some housecleaning?

I prefer just to use synaptic, but now you have to install that as it is not a default app.
       Determine your current kernel, be sure not to purge current:
uname -a
uname -r
In synaptic or software center search for linux-image to choose to purge old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
    
       HOWTO: Remove Older Kernels via GUI (or CLI) 
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)
[http://www.liberiangeek.net/2010/07/remove-kernel-ubuntu-10-04-lucid-lynx-grub/](http://www.liberiangeek.net/2010/07/remove-kernel-ubuntu-10-04-lucid-lynx-grub/)

    
And if you have all those kernels you may have lots of log files and other cruft.
       HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

    
       HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by ZoCo on 2013-01-28
> **oldfred said:**
> Looks like it may be time to do some housecleaning?

I prefer just to use synaptic, but now you have to install that as it is not a default app.
       Determine your current kernel, be sure not to purge current:
uname -a
uname -r
In synaptic or software center search for linux-image to choose to purge old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
    
       HOWTO: Remove Older Kernels via GUI (or CLI) 
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)
[http://www.liberiangeek.net/2010/07/remove-kernel-ubuntu-10-04-lucid-lynx-grub/](http://www.liberiangeek.net/2010/07/remove-kernel-ubuntu-10-04-lucid-lynx-grub/)

    
And if you have all those kernels you may have lots of log files and other cruft.
       HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

    
       HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

I do have Synaptic package manager installed
I used the uname -a and uname -r to find out my current version (attachment1)
but when I do a search for linux-image I find multiple results that match my current version ( all have green check boxes next to them, see attachments 2 & 3) are these the ones to keep and get rid of the rest, sorry I just want to be really clear on what I'm supposed to do here lol I've had enough pc anxiety in the last 24 hours
I re-read the instruction at the link you sent, I see all the green ones are the ones installed these are what I want to remove, bar the one marked 57 because that is my current version, Is this correct?

---

### Post by oldfred on 2013-01-28
You want to keep -36 and maybe -35 just to have another as backup. Purge all the others. Or mark for complete removal.

I have 64 bit so my version is not quite the same. no PAE.

fred@A105-Precise:~$ uname -r
3.2.0-36-generic

---

### Post by ZoCo on 2013-01-28
> **oldfred said:**
> You want to keep -36 and maybe -35 just to have another as backup. Purge all the others. Or mark for complete removal.

I have 64 bit so my version is not quite the same. no PAE.

fred@A105-Precise:~$ uname -r
3.2.0-36-generic

It worked a charm thank you so much for your help oldfred,
my grub menu is all clean and tidy now :-D
and thanks again to ibjsb4,
I applaude you both =D>

---

### Post by Bucky Ball on 2013-01-28
I use Grub Customizer to keep things neat:

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

;)

---

### Post by ZoCo on 2013-01-29
> **Bucky Ball said:**
> I use Grub Customizer to keep things neat:

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

;)

oh cool, thanks Bucky Ball:-D

---

