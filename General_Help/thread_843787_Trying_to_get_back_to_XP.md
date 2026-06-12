---
title: "Trying to get back to XP"
date: 2008-06-28
forum: General Help
---

### Post by Edigido on 2008-06-28
So a while back, I had switched to Ubuntu, because I liked the idea and the way it looked.  Also a friend of mine had it, and had expressed how much he liked it.  Now I too love the OS.  But the problem is that there are multiple programs that I need that are only windows operable (Itunes, Video Games, and multiple office programs for school).  I know that there's Wine, but that only works some of the time, and I need something that works all of the time.

Now while the best idea would be to have it dual booted with XP (that way I can get the best of both worlds).  

If the dual boot isn't possible, then just getting back to XP would be the best.  I don't have a live CD, but could recreate a disk from the internet.  I might have an XP start up disk, but it seems to be only for a Dell PC, while I've got a Lenovo.

---

### Post by rafe123 on 2008-06-28
A) Do you have XP still installed?
 - if so, what drives are each (Linux and XP) installed on?

Dual boot is definitely possible. There are numerous links out there. Here are a few I have found:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
[http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-and-windows-ntxpvista/](http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-and-windows-ntxpvista/)
[http://www.dedoimedo.com/computers/dual_boot.html](http://www.dedoimedo.com/computers/dual_boot.html)
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Good luck!

---

### Post by Journeyman on 2008-06-28
if you have no issues reinstalling ubuntu then that is the best option. otherwise you would need to resize your parition then fix the mbr.

First install XP when you create the parition make sure you don't use the whole disk (most people do half and half).  After that is finished install Ubuntu, now there should be an option to install on the rest of the free space or if you used up all the space there is an option to resize the partian.  Then once you finish installing ubuntu it will automaticly configure grub, when you first boot up you will have the option to boot windows or linux.

good luck, let us know if you need anything else ;)

---

### Post by VMC on 2008-06-28
> **Edigido said:**
>  I know that there's Wine, but that only works some of the time, and I need something that works all of the time.

Now while the best idea would be to have it dual booted with XP (that way I can get the best of both worlds).  

If the dual boot isn't possible, then just getting back to XP would be the best.  I don't have a live CD, but could recreate a disk from the internet.  I might have an XP start up disk, but it seems to be only for a Dell PC, while I've got a Lenovo.

Dual boot is possible. It would be best to install XP first then ubuntu second. Regarding Wine. It works all the time, just not on all programs.

I'm not sure I understand where you are about the Dell, IMB and XP disk. Can you install XP?

---

### Post by Edigido on 2008-06-28
I started out in XP, and am now in Ubuntu.  When I had installed Ubuntu the computer died half way through the night (my idiot self had fallen asleep and didn't plug it into the wall).  I had woken up the next morning to find all of my data gone, and just went ahead with the Ubuntu Installation.

---

### Post by Edigido on 2008-06-28
Okay, I just tried installing XP straight from the disk after I had restarted the computer itself, and it says that there is no Hard Drive/Disk detected.  I'm pretty sure this is due to the partition taking up too much space (could be wrong).  I have tried resizing the partition, but it's mounted and I'm not sure how to unmount the partition.  Any ideas? (or suggestions to a secondary route?)

---

### Post by bear54 on 2008-06-28
I would try Open Office for your school work needs. Open office has everything you will need and works great with Ubuntu.:)

---

### Post by Edigido on 2008-06-28
Okay, that's a good idea actually.  Do those save in in the word formats as well (for programs/papers that may need to be sent to teachers).

Any ideas for Itunes?

---

### Post by hopelessone on 2008-06-28
Do you know about VirtualBox? you can run windows inside linux without having to Duel Boot...

I do it and its fantastic..

---

### Post by Edigido on 2008-06-28
No I don't...it can work like that?!  That would solve most if not all of my problems.  Is it in Synaptic?

---

### Post by hopelessone on 2008-06-28
[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

Hope that helps.. :)

---

### Post by wthex on 2008-06-28
> **Edigido said:**
> Okay, I just tried installing XP straight from the disk after I had restarted the computer itself, and it says that there is no Hard Drive/Disk detected.  I'm pretty sure this is due to the partition taking up too much space (could be wrong).  I have tried resizing the partition, but it's mounted and I'm not sure how to unmount the partition.  Any ideas? (or suggestions to a secondary route?)

Edigido,

Make sure you read as much as you can about this before you start your dual boot system. Windows must be installed first, however in your case you may have ext3 file system on your hd. Windows will not install on that filesystem. You will need an ntfs file system for windows to install.

Plan your partition sizes, format them accordingly, install windows then install the Ubuntu distro.

It's not really that hard to do if you have a plan, and to formulate a plan you're going to have to read about the procedure.

A good place to start is in rafe123's post - follow those links and do some reading.

> **rafe123 said:**
> Dual boot is definitely possible. There are numerous links out there. Here are a few I have found:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
[http://digitalgraphy.wordpress.com/2...ows-ntxpvista/](http://digitalgraphy.wordpress.com/2...ows-ntxpvista/)
[http://www.dedoimedo.com/computers/dual_boot.html](http://www.dedoimedo.com/computers/dual_boot.html)
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Good luck!

Again - Good luck!

---

### Post by VMC on 2008-06-28
> **hopelessone said:**
> Do you know about VirtualBox? you can run windows inside linux without having to Duel Boot...
I do it and its fantastic..
I'll have to try this. I keep seeing a lot of topics that have issues with virtual machines.

> **Edigido said:**
> Okay, I just tried installing XP straight from the disk after I had restarted the computer itself, and it says that there is no Hard Drive/Disk detected.  I'm pretty sure this is due to the partition taking up too much space (could be wrong).  I have tried resizing the partition, but it's mounted and I'm not sure how to unmount the partition.  Any ideas? (or suggestions to a secondary route?)

I think the problem here is Grub and the Linux partitions confusing Windows installer. This is the second time I've run across this same issue.

If you want to start over with XP first and ubuntu second you need to delete all partitions AND fix the mbr back to Windows. I use Ghost's gdisk. Much simpler and faster. Dos's fdisk is a gui type.

hopelessone, might have the best solution. That way, if you realize that at some point you no longer need Windows you can remove the virtual file. Personally, I've been Windows free for a couple of months now :)

---

### Post by Edigido on 2008-06-29
Thank you so much!  The virtual box is working beautifully, and now I just need Mozilla and a few other programs and it'll work just like I want it to.

---

### Post by flytripper on 2008-06-29
yes you may need this version for usb usage with your ipod   [here.]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

and if it doesnt allow you to connect the virtual machine to the ipod then follow this thread [here.]("http://ubuntuforums.org/archive/index.php/t-430735.html")

---

### Post by Edigido on 2008-06-29
Okay, so I'm not getting any audio at all in the Virtual Machine, is this normal?

---

### Post by WRDN on 2008-06-29
> **Edigido said:**
> Okay, so I'm not getting any audio at all in the Virtual Machine, is this normal?

Thats normal. To solve this problem, just open the settings window for the entry (in this case, XP), select the Audio option in the left hand panel, and select "Enable Audio" (or words to that affect).
If you have any sound issues, just select a different driver.

---

### Post by Edigido on 2008-06-29
Okay, Itunes also won't register the CD that I put in.  I'm pretty sure I enabled the drive, but I'm not sure.

---

### Post by theshadowwithanmp5n on 2008-06-29
wine windows emulator...
not to sound condescending,
if not try the virtualbox.

---

### Post by Edigido on 2008-06-30
I'm used both, and am currently using the Virtual Box.  But Itunes won't recognize the cd.

---

### Post by theshadowwithanmp5n on 2008-07-05
there's an itunes app
it's called gtk-pod
beware, it's a little volatile but it works
the worst that can happen is it renames a small bit of your mp3 files into their system names, such as SAWA.mp3 
in that case, it's not that hard to rename them.

---

