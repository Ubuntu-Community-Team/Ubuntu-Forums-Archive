---
title: "How can I work around this boot loader issue?"
date: 2006-09-11
forum: General Help
---

### Post by Roasted on 2006-09-11
Long story short:

I had 2 ide drives in my system. Master - XP, Slave - Linux.

Then I upgraded and went to SATA drives. Drive A of SATA is the main drive, drive B of SATA is the backup. No Windows this time around.

What my plan is, is I want to use the IDE XP drive + the two SATA drives for Linux in a dual boot setup. Reformatting is not an option, so if I have to choose I'll drop XP. 

But when I plug in my IDE XP drive + my two SATA drives, I get error 17 at the boot load screen. If I use both of the IDE drives, it's fine and gives me the choice of OS to boot to.

Question is, how can I configure grub to accept my IDE XP drive + my SATA Linux drives?

---

### Post by Herman on 2006-09-12
Roasted,
First, I have to admit, I don't have a computer with Sata drive here, so I do not feel qualified to give you any exact, specific help. I wish I could.
However, I might be able to give you some general advice that might get you on the right track.
Quoted from the Gnu Grub Manual,
> 17 : Cannot mount selected partition. This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.           If you get this error when trying to boot Linux, check your grub conf. or menu.lst file and make sure to check your operating system entry's 'root (hdx,y)' details are correct. (Most likely in your instance, the hard disk numbers are the ones that are being changed).
  
Why not try booting and going into Grub's Command Line Interface and using Grub to do the work for you and have Grub take a look around your computer and report back what it calls your hard disks and partitions and how they are numbered?
If you take notes at the same time, you should be able to boot your operating systems from the Command Line, and using the notes you made when making a successful boot-up, then edit your menu.lst file with the same commands.
To see more information about how to go about doing that, [Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").

Any feedback about whether that helps you or not and how that how-to might be improved would be welcome. I would be interested in how someone with Sata and IDE mixed gets along with it.

Also, Super Grub Disk might be  handy, you can always get a Grub Command Line with Super Grub Disk, or use it in Menu mode. whichever you prefer.
Thanks, and Regards, Herman

---

### Post by Roasted on 2006-09-12
How can I boot into the command line interface without booting into the system? I don't know what to do once I get the error 17. And what would I do at that point, get into my grub config file and post the findings here?

In essence, grub is working fine with my IDE XP and IDE Linux drive. But I'm essentially changing the Linux drive from IDE to SATA, and this is where I'm getting the grub error. So that's where I'm left...

---

### Post by Herman on 2006-09-12
If you just get the error 17 message right away, and no Grub Menu at all, then you can always use a [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php"), or any Grub CD or Floppy disk, to get a Grub Command Line with, you would just need to press your 'c' key from any Grub Menu and you will have Command Line Grub.

---

### Post by Roasted on 2006-09-13
Okay. I'm one step closer, yet no cigar.

Just to refresh you guys, I had XP and Linux on TWO IDE drives. I took the Linux IDE drive out, and now I added a pair of SATA drives. One is a backup, one is main. In a nutshell, I removed the IDE Linux drive, and replaced it with the SATA Linux drive.

My buddy helped me out a bit. What we did is we edited two files in the grub directory. First of all, the device.map file we added a drive.

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/hdc

HD0 is my main SATA drive, HD1 is my backup SATA drive (non bootable), and HD2 is my IDE Windows XP drive.

Now, let's take a look at my menu.lst.

At the bottom, I was instructed to add the following for my Windows drive. 
I was also instructed to add it below the ### END DEBIAN AUTOMAGIC line that you see below.

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows
root		(hd2,0)
savedefault
makeactive
chainloader	+1

Now, when I reboot, I have the list to select Windows XP or Linux. When I select Windows XP, I get the following error.



Booting Windows XP
root (hd2,0)
File system type unknown, partition type 0x5
save default
makeactive

Error 12: Invalid Device Requested

press any key to continue...



So, we're one step closer. At least I have Windows XP listed. But I cannot successfully boot into it.

Why?

---

### Post by g4c9z on 2006-09-13
In my menu.lst, the windows entry is below this:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

Do you also need that divider section?  Admittedly, though, I don't know what it means, and I don't know much about your specific situation.

---

### Post by Roasted on 2006-09-13
I wonder what the purpose is of that bit of info you posted above? I mean, do you think it'd solve my problem? (not trying it tonight) I'm no grub expert, but I just can't see how it'd work. Oh well, tomorrow is another day. :D

---

### Post by Herman on 2006-09-14
Roasted,
I see what g4c9z means, you have omitted these lines, they belong after the end of the debian automagic kernels list, and g4c9z might be right, I think you should paste them in too, ```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root
```Also, since you have NTFS in WIndows by the looks of things, you can change 'root' to 'rootnoverify', that doesn't always make a big difference, but it has been reported to do the trick sometimes.
As well as that, since you are booting Windows from a non-first hard disk, you will also need to use a 'map' commands, to trick Windows into thinking it is booting from a first hard disk.

So you should edit it like;
```
 ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

title        Windows
rootnoverify        (hd2,0)
map                    (hd0) (hd2)
map                    (hd2) (hd0)
savedefault
makeactive
chainloader    +1
``` If that still doesn't "do it" :D, Try experimenting with Grub's Command Line again, [Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_boot_Windows_using_GRUBs_CLI").
 It's easier to experiment with the command  line because it often give useful feedback and if you fail in an attempt to boot, you can try again immediately, rather than have to boot up, edit menu.lst and reboot again.

If you are still having problems, the output from the command 'sudo fdisk -lu' could be a big help too, ```
sudo fdisk -lu
```

See how you go now, good luck, Regards, Herman :D

---

### Post by Roasted on 2006-09-14
Here's my output from fdisk -lu.


Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      996029      497983+   5  Extended
/dev/sda2   *      996030   490223474   244613722+  83  Linux
/dev/sda5             126      996029      497952   82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63      996029      497983+   5  Extended
/dev/sdb2          996030   490223474   244613722+  83  Linux
/dev/sdb5             126      996029      497952   82  Linux swap / Solaris

Disk /dev/hdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63   398267414   199133676    7  HPFS/NTFS
jason@jason:~$



I'm still getting error 12. I tried it with "root" and "rootnoverify" under the Windows tag.

Just for clarification, there's 3 drives here. The 251 gig drives are my SATA drives. One is bootable and has linux on it, the other is just hooked up and I use it for rsyncing (it's not bootable, but contains backups of pictures and whatnot). The 203 gig drive is my Windows drive, which is an IDE drive that I'm trying to boot to.

---

### Post by turbojugend_gr on 2006-09-14
You need to map the drives, so edit menu.lst's windows section like this:```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
rootnoverify		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

That should work, just in case though be sure to keep a backup. ;)

---

### Post by Roasted on 2006-09-14
Something I'm not sure of. Take a look here:


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
rootnoverify		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

Second line, /dev/sdb1... is that right? Should it be sdb1? Shouldn't sdb1 be my Windows drive?

---

### Post by turbojugend_gr on 2006-09-14
> **Roasted said:**
> Something I'm not sure of. Take a look here:


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
rootnoverify		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

Second line, /dev/sdb1... is that right? Should it be sdb1? Shouldn't sdb1 be my Windows drive?

Well first of all it is quated so it means nothing to Grub (the ## signs tdo that), it is info for your understanding nothing more... and after all yes it is supposed to name the windoz apartition Unix-wise so it is the second drive 1st partition right?

---

### Post by Roasted on 2006-09-14
So should my entire bottom of the list look like this?




### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Home Edition
rootnoverify (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

---

### Post by turbojugend_gr on 2006-09-14
yup, try it and plz tell me how it went!

---

### Post by Roasted on 2006-09-14
[IMG]http://i2.photobucket.com/albums/y36/Roasted/P1030048.jpg[/IMG]

---

### Post by Herman on 2006-09-15
Okay then , it thinks your (hd2,0) is an invalid device eh?
Well what feedback do you get when you are booting up and when you are at your Grub Menu, you press your c key for a [Grub Command Line]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and enter 'find /boot.ini' ```
find /boot.ini
``` If Grub cannot find boot.ini at all,  then you should go back through your BIOS and make sure your third hard disk is properly detected and set up in your BIOS.
If Grub does find boot.ini, but says it's on some different disk number or partition number, then try replacing (hd2,0) in your booting commands with whatever number Grub detects it as.
You should be able to boot it from Grub's Command Line with the same commands you use in menu.lst, but you can try changing them a little until you get them working properly, especially the hard disk number if your grub thinks it should be called it some other number. ```
[COLOR=black]rootnoverify (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
boot[/COLOR]
```

---

### Post by Roasted on 2006-09-15
How do I get to grub's command line? Do I use one of these other things listed besides the regular Linux operating system? 

[IMG]http://users.bigpond.net.au/hermanzone/p2d/24fat32.png[/IMG]

---

### Post by turbojugend_gr on 2006-09-15
Under the menu, outside the boarder.. Where it says: USE THE ARROW KEYES TO SELCET WHICH ENTRY IS HIGHLIGHTED....PRESS ENTER TO........OR "C" FOR A COMMAND LINE. So it syas you have to prees the "c" key in order to see the command line. 

PS: It is possible that grub locates your drives in vica versa, in my system It does so, so try deleting the 2 map lines. This case is usual if you install a second drive (especially a STA one) after you have "grubbed" the mbr of your old one.... in simple words. if you have bought a disk after installing ubuntu this may be the case.

---

### Post by bulldog on 2006-09-15
The solution could be simple.
Look in your BIOS and set the drive with XP as the drive to boot from.
[hd0.0]

You should have that option in your BIOS.
IDE drives are refered to as hd and sata drives are sd.

But when you put more drives in your computer you need to alter fstab too because the drives are changed.

I have IDE and Sata mixed up and had it sorten out which was a pain but when you look back it's quite simple realy.

Windows wants to start from the first hd but can be fooled by the mapping thing.

It's suggested before,just find out how your configuration is after you put in your sata disks.
Make a note of their names and alter menu.lst and fstab to what it's called with the new drives.
Remember that GRUB uses other names as fstab!!

---

### Post by Roasted on 2006-09-16
From grub's command line, I entered: find /boot.ini.

The response: Error 15, file not found.

I also noticed that the "name" for the Windows drive when I look in system-admin-disks, the Windows drive is HDC. Does that matter? The error I was getting when I try to boot from the Windows drive is the following:

[IMG]http://i2.photobucket.com/albums/y36/Roasted/P1030048.jpg[/IMG]

Since it says HD2, is that okay? Does grub think that HD2 is the Windows drive, when it's really HDC?

---

### Post by turbojugend_gr on 2006-09-16
It should be HDC, as it's 3rd disk. If for instance it was the second partition of the 5th disk Linux would call it : "hdE2" while grub would call this one (hd4,1) you see Grub starts counting from 0 (zero) and only uses number figures, Linux instead prefers using a letter for the disk and starts counting from 1 (one).

That's all with the Trivials, so I think you sould try this:

1. Get into grub menu (or in other words boot up your machine).
2. Press the 'c' key so you enter the command line of Grub.
3. Then issue the following commands:
```
grub>   rootnoverify (hd2,0)
grub>   makeactive
grub>   map (hd0,0) (hd2,0)
grub>   map (hd2,0) (hd0,0) 
grub>   chainloader +1
grub>   boot
```
4. If that doesn't work try alterning the "rootnoverify" command to "root"
5. If that doesn't work either reapeat the process again omitting the 2 "map" commands
6. Post what's going on back here so I help you on that. If you can take notes on each error that would be extremely helpful to understand what's your problem in depth.

PS: I turn my attention on the command line so you don't have to change and backup your menu.lst file all the time. It is safer and quicker so we will solve this one (hopefully) sooner this way. Keep posting so you get rid of this as soon as possible. Maybe sb else has an idea, if mine go to the trash bin... ;)

---

### Post by Roasted on 2006-09-19
I got an error when I did the makeactive line. It said something about an unknown device requested, or something? I don't know, didn't work.

what else can I do? It's been a few days since I looked at this and now I feel like I forgot everything I've done already. :mad:

---

### Post by turbojugend_gr on 2006-09-20
Don't worry 'bout forgetting I remember what is done here (according to this thread of course I don't know if you did anything else).

About the error now, try repeating the same commands (from my previous post) ommitting the makeactive command, all the others command you do issue them, actually try ommiting the map commands if that doesn't work also.Again post the output.

---

### Post by Roasted on 2006-09-20
I get "Loading stage2Read Error" when I do that.

I still don't understand this. Quite frankly, to me it seems like a misnamed drive. I can't see why I can't erase the old drive that was on grub, and put in the drive ID for the new one. Then, why wouldn't Grub pick it up? It's just overwelming, seeing all of these different menus and device lists I have to edit and with certain coding and shit. I just find it hard to believe I don't have the option to alter the drive name...

---

### Post by turbojugend_gr on 2006-09-22
OK, from what I 've seen, and grub realted these are too much, you should definately be able to boot by issuing the following commands: ```
rootnoverify (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```Or at least that's what I believe according to your sayings. SO since you are not able to boot your winxp, I end up you are mistaken somehow.
You posted that Linux recognize your winxp partition as hdc, which in grub it is named (hd2,0). So i wonder if you might have another partition on that damn disk so maybe you should alter (hd2,0) to (hd2,1) for instance. Another case is your BIOS might detect that disk differently, so (hd2,0) might even be (hd3,0) or (hd1,0) and so on, but you said you can't see the boot.ini.

We can clear things out though, answer plz all of the following questions:
1. How do you boot into winxp at the moment? (do you unplug the drives maybe?)
2. How do you boot into ubuntu ? (although I am pretty sure you just select it from grub, no harm in asking.)
3. Can you post your entire /boot/menu.lst plz, so if I come up with sth I don't have to ask for info first then post it.

Plz anser the above and I hope we can get this sorted out, it is definatelly sth messed up, we will see...

---

### Post by adrian15 on 2006-09-22
> **Roasted said:**
> I got an error when I did the makeactive line. It said something about an unknown device requested, or something? I don't know, didn't work.

what else can I do? It's been a few days since I looked at this and now I feel like I forgot everything I've done already. :mad:

Hi Roasted. Do not trust on your device.map is nonsense when you boot grub.
Let's see. You're going to do two things and you copy-paste results here and then me and all the other will be able actually to help you.

Press the c key when booting grub so that it shows the command line.
```

cat (hdPRESSTABULATORKEYHERE

```
It will show you the hard disks that Grub detects.
This will give us a clue of what disk is which one.

Then let's supppose that you read:
```

Possible completions are:
hd0
hd1
hd2

```
then you should do:

```

cat (hd0,PRESSTABULATORKEYHERE

cat (hd1,PRESSTABULATORKEYHERE

cat (hd2,PRESSTABULATORKEYHERE


```

This will show you the partitions that are in each of the hard disks, you will be able to see their filesystems types too.

With this information you will be able to solve your problem or at last make our task of helping you easier.

What Grub hard disks sees as hd0, hd1 or hd2 can be changed by the bios or when you plug or unplug another disk so repeat the operation when needed.

And... Do not use the makeactive or the savedefault commands when you are making tests. Once everything boots you can experiment with this commands.

adrian15

P.S.: When you see PRESSTABULATORKEYHERE it means that you should press the tabulator key which is usually found above the CAPITALS BLOCK key. If it does not work at once press it again.

---

