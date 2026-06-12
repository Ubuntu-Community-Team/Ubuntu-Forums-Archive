---
title: "Error code 12"
date: 2008-01-29
forum: General Help
---

### Post by timsmish on 2008-01-29
I installed ubunto last night...following all instruction to the tee...( I think)  LOL
I have sony vaio with preinstalled vista premium,I am trying the dual boot method when I turn my pc on i get 5 options for startup...when I choose windows vista/Longhorn...It wont boot just gives error code 12 and then a dos screen...I can boot ubunto no problem...Any Ideas where I am going wrong....

---

### Post by danwood76 on 2008-01-29
can you post the output of these two commands in the terminal please:
```

sudo fdisk -l
cat /boot/grub/menu.lst

```

With this info we should be able to fix your boot problem.

regards,
Danny

---

### Post by timsmish on 2008-01-29
I will do it tonight when I get home...Very new to all this (curse my inquisitive mind) LOL, I just can't leave well enough alone . how do I post these results?

---

### Post by gvartser on 2008-01-29
I agree that this would give us info to help out, but the strange thing is that he can boot into some kind of dos mode.

Ill see forward to seeing the output of the commands..

/g

---

### Post by timsmish on 2008-01-29
correct when I try to boot vista/longhorn I get a c prompt

---

### Post by danwood76 on 2008-01-29
are you sure its a dos prompt and not a grub prompt?
they do look similar and there is no way you would get a C prompt from a vista partition.

regards,
Danny

---

### Post by timsmish on 2008-01-29
your probably right...can I type anything into the grub prompt that would allow me to boot Vista/Longhorn?

I have also lost my @ key on my keyboard with ubunto

---

### Post by danwood76 on 2008-01-29
do you use a uk keyboard?
because its probably set to us and your @ key has been switched with " (shift 2).

that can be reconfigured very easily.
we'll tackle that once you have windows back :)

regards,
Danny

---

### Post by timsmish on 2008-01-29
sounds Good thanks for being here for us NEWB's...

---

### Post by danwood76 on 2008-01-29
Everyones got to start somewhere. ;)

---

### Post by timsmish on 2008-01-29
> **danwood76 said:**
> can you post the output of these two commands in the terminal please:
```

sudo fdisk -l
cat /boot/grub/menu.lst

```

With this info we should be able to fix your boot problem.

regards,
Danny

Ok Guy how do I do this

---

### Post by danwood76 on 2008-01-29
click Applications top right hand corner then go to accesories and click terminal.
this will open a command prompt window.

copy each line one by one into the window pressing enter after each and post the result of both commands.
After the first one you will have to enter your sudo password (this is just your standard login password)

regards,
Danny

---

### Post by timsmish on 2008-01-29
first command
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc79474a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       23568   189309928+  83  Linux
/dev/sda2           23569       23830     2104515    5  Extended
/dev/sda3   *       23831       24321     3943957+  83  Linux
/dev/sda5           23569       23800     1863508+  82  Linux swap / Solaris
/dev/sda6           23801       23830      240943+  82  Linux swap / Solaris

Disk /dev/mspblk0: 489 MB, 489160704 bytes
32 heads, 32 sectors/track, 933 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mspblk0p1   *           1         932      476683+   6  FAT16

---

### Post by timsmish on 2008-01-29
second command

initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by timsmish on 2008-01-29
anyone know what I did wrong

---

### Post by timsmish on 2008-01-29
can someone read these code posts and tell me if vista still exists and if I amable to boot into it.
Please lol

---

### Post by timsmish on 2008-01-29
now when I try to boot into vista longhorn it says error code 12 invalid device requested
I am not trying to be a pain but I would like to see if this vista is recoverable or should I format everything and start over:(

---

### Post by timsmish on 2008-01-29
please excuse the frustration here ....But where are all the helpful people that i see being touted....:confused:

---

### Post by danwood76 on 2008-01-30
I hate to dissapoint you but it looks like youve overwritten your vista partition with linux.
There are no NTFS partitions on your first drive, least of all on (hd0,1) where grub is trying to boot from.
If you re install vista, on the partitioning screen in the installer make sure you leave some space free which you can later use for ubuntu.

I hope you didnt loose anything useful.

it looks like you will have to start over.

> But where are all the helpful people that i see being touted

quite often if a thread has 0 posts it will get more help that a thread with lots of posts.
This is a very fast pased forum with a lot of people needing help.
Generally if someone starts helping you they will continue to do so, but obviously I can only post when im online :)

regard,s
Danny

---

### Post by gvartser on 2008-01-30
> **danwood76 said:**
> quite often if a thread has 0 posts it will get more help that a thread with lots of posts.
This is a very fast pased forum with a lot of people needing help.
Generally if someone starts helping you they will continue to do so, but obviously I can only post when im online :)

regard,s
Danny

Well put.

/G

---

### Post by timsmish on 2008-01-30
Not upset at you guy's just frustrated with myself (my appologies)
alright  I messed around for over 8 hours last night and got no where. I tried fixing the drive with my xp pro cd....It runs loads all the startup files, and when I tell it to format the drive it say's that it doesn't exist (no drives found...What can I do?

---

### Post by timsmish on 2008-01-30
Can I uninstall ubuntu and start over...if so I how do I format my drive from the live cd to ntfs format... so my hdd gets recognized... step by step if possible.

---

### Post by danwood76 on 2008-01-30
The XP CD should recognise the hard disk. But it may not if the drivers for you hard disk controller are too new.

Do you not have a vista recovery CD you can chuck in to resinstall vista?
It would return your PC back to the way it was when you bought it if you do.

regards,
Danny

---

### Post by timsmish on 2008-02-01
No I didn't have one...So I created a sliptreamed XP cd with the sata drivers that I needed to recognize my HDD...Then I had a Vista upgrade cd that i was able to use....Everything is back to normal now...Sony vaio...Sony doesn't offer much in the way of driver software on the internet....But I found what I needed with a little (alot) of searching LOL. I guess I will have to do alot more reading if I am going to have a dual boot system...I really wanted to try this linux thing though...It looks pretty cool the things you can do with it...is their a link for first timers on how to set dual boot properly with vista....
P.S thanks for the help.

---

### Post by danwood76 on 2008-02-01
What you should do is resize your main partition using the Vista Disk Management tool.
(Control Panel -> Administrative Tools -> Computer Management, then disk management down the left side)
resize the main partiton so you have around 10 GB free.

Then try to install ubuntu, this time you should be able to select something along the lines of 'Use guided partitioning using free space' or something along those lines.
It should then setup fine on the extra space.

I found a guide for you doing these steps:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

best regards,
Danny

---

