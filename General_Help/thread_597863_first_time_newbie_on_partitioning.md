---
title: "first time newbie on partitioning"
date: 2007-10-30
forum: General Help
---

### Post by hydroman on 2007-10-30
i accidently over partitioned my drive while installing ubuntu.

my computer came preinstalled with vista and so i wanted to dual boot for the first time with ubuntu.

my plan originally was to make vista have 314 gigs of hard drive  space and ubuntu have around 50 gigs hard drive of space, however it back fired and so now that i have installed ubuntu with 314 gigs of space while vista has 54. now vista is on the verge of losing all of its space as i have alot of files with in the operating system.


**offtopic:** i have D-Link air plus G DWL-G122 wireless usb adapter (rev.B) and ubuntu has picked noticed this as it gives me available network connections through my Region  .....but when i try to connect to my router it doesn't work. i put in the password but there was no luck in connecting.

---

### Post by AlexThomson_NZ on 2007-10-30
gparted (Gnome Partition Editor) is a great program for this (think of it as the Linux version of Partition Magic on Windows)

In a terminal type "sudo apt-get install gparted" to install it.  From this you should be able to resize the partitions without losing data

---

### Post by hydroman on 2007-10-31
i tried that in the terminal but i don't think it worked and so i was given the following output: 
hydroman@hydroman-desktop:~$ sudo apt-get install gparted 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Package gparted is not available, but is referred to by another package. 
This may mean that the package is missing, has been obsoleted, or 
is only available from another source 
E: Package gparted has no installation candidate 
hydroman@hydroman-desktop:~$  



-Am i suppose to install gparted from the internet? if so i can't cuz for some reason wehn i try to connect it doesn't work, though ubuntu does recognize my network adapter.

---

### Post by plantman on 2007-10-31
> **AlexThomson_NZ said:**
> gparted (Gnome Partition Editor) is a great program for this (think of it as the Linux version of Partition Magic on Windows)

In a terminal type "sudo apt-get install gparted" to install it.  From this you should be able to resize the partitions without losing data

I have gparted but I can't seem to unmount the disk I want to enlarge. I started out with WinXP and did an install of Feisty. I used this dual boot for a little while until I became comfortable with Linux. (I am a new-newbie!) In the process, I upgraded to Gutsy and decided to dump XP. I am working out the bugs on Gutsy and want to make this partition larger and either dump or decrease the Feisty OS. Can you or someone else tell me exactly how?
Thanks:confused:

---

### Post by hydroman on 2007-10-31
**Off topic: **u made a terrible mistake dumping XP.
you should have kept it in your dual boot. many (almost all) softwares are exclusively made for microsoft windows..........



**On topic:** but anyways can someone help how to increase my partition size as i made a mistake during the partitioning step...

---

### Post by Orion2014 on 2007-10-31
You should really burn GParted to a disk and boot from it to partition your drives. That way you wont have to worry about what's mounted and what's not. :guitar:

---

### Post by hydroman on 2007-10-31
huh? incase u didn't know, i am a total newbie when it comes to linux so please explain to me what u meant.........though i am a harcore microsoft windows user!!

---

### Post by AlexThomson_NZ on 2007-10-31
Go and download a LiveCD from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Burn the image to a CD and boot from it, that way it is not actually mounting the partitions so you can resize them ok.

(Sorry I forgot about that :) )

---

### Post by plantman on 2007-11-05
> **AlexThomson_NZ said:**
> Go and download a LiveCD from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Burn the image to a CD and boot from it, that way it is not actually mounting the partitions so you can resize them ok.

(Sorry I forgot about that :) )

:)Thanks!!! I did that and have been able to dump everything I don't need and clean up my hard drive. I do not and will not want to keep Win XP. I have been able to do everything I want to do with LInux and have GLADLY cut the Windows cord!

---

### Post by AlexThomson_NZ on 2007-11-07
Good on ya mate! :)  No going back now...

---

