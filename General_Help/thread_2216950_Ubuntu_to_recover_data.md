---
title: "Ubuntu to recover data"
date: 2014-04-14
forum: General Help
---

### Post by andy_p2 on 2014-04-14
Hi All,

I'm new with using Ubuntu. I was hoping someone could help me with this issue. I was using windows 7 with an external WD 3Tb hdd to store my movies and files. I recently bought a 4Tb hdd and a Dual hot swap dock. Instead of moving the files to my 4tb hdd first I took the hdd out of the 3tb casing. I then put both 3 and 4tb on the dock and connect to PC. Both shows up as unallocated disk on windows and renamed both. The 4tb works fine since it had no information while the 3tb asked me to reformat which i didn't. Now I can't see any files on the 3tb hdd and putting it back in the casing didn't do anything either. 

After using a few programs to scan and try to recover data it didn't help much. I researched online and some say Ubuntu can restore my data but it doesn't detect the 3tb hdd. What command lines can i run in order to view the files in this hdd and move all the data to my 4tb hdd? Please help. 

Thanks before hand.

---

### Post by sdowney717 on 2014-04-14
I would start with gparted to view the drive

sudo apt-get install gparted

then run gparted.
In the upper right corner a drop down box will select drives.
If the bios sees the drive, ubuntu will see the drive.

Does your bios detect the drive?

---

### Post by andy_p2 on 2014-04-14
In windows the drive shows up but when I click on it, it asks to reformat the drive.

---

### Post by andy_p2 on 2014-04-14
the drive shows up in Gparted. what can i do next?

---

### Post by sdowney717 on 2014-04-15
[QUOTE=andy_p2]Hi, the drive shows up in Gparted. What shall i do next to recover my files? Thanks for your help[/QUOTE]
Does gparted show the graphical partition as it exists?
Perhaps all you nee do is

open file manager
look down left panel
find your drive
click it and it will mount and show the files.
Extra drives do not automatically mount.

If it is not there, in gparted there may be a message about the drive. exclamation mark, something.

if there is gparted might need to fix a flag or gparted will say it needs a cleam mount to run some command

can you post a screenshot of the drive , screenshot is a program. post it here using the forum

---

### Post by andy_p2 on 2014-04-15
Will attach picture this afternoon when i get home.

---

### Post by andy_p2 on 2014-04-15
Here is the screenshot of the error. the 2.73tb of data is the what i'm trying to recover.

---

### Post by sdowney717 on 2014-04-17
Ok, I see the picture.
can you click on the exclamation, does it give any more information?
It is saying this is an unknown file system.

---

### Post by sdowney717 on 2014-04-17
you might need to use testdisk to rebuild the partition table.

It works for some people, also note gparted for them showed unknown file system.
Seeing yours was windows 7, should have been ntfs

[http://www.absolutelytech.com/2010/09/23/solved-unknown-filesystem-in-gparted-in-ubuntu/](http://www.absolutelytech.com/2010/09/23/solved-unknown-filesystem-in-gparted-in-ubuntu/)

---

### Post by Mark Phelps on 2014-04-17
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from [http://getdata.com](http://getdata.com).
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to their website, you can compare versions and features.

Your data ... your money ... your choice.

---

### Post by sdowney717 on 2014-04-17
good idea to use windows based program.

Couple years ago I used one of these.

EaseUS Partition recovery
[http://www.easeus.com/](http://www.easeus.com/)
Eassos  Recovery free
[http://download.cnet.com/Eassos-Recovery-Free/3000-2248_4-75718351.html](http://download.cnet.com/Eassos-Recovery-Free/3000-2248_4-75718351.html)

Partition Guru Pro.
[http://www.eassos.com/partitionguru/download.php](http://www.eassos.com/partitionguru/download.php)
I forget which one worked, but it worked well and it was free.

Installed them all and ran them.  Some showed what it would do but cost money to complete the repair. Some showed what it would do and fixed it for free.

---

### Post by stalkingwolf on 2014-04-17
I have used a free version of pandora on windows that worked really well.

---

### Post by Mark Phelps on 2014-04-17
If you want a free Windows data recovery program, try Recuva.

---

