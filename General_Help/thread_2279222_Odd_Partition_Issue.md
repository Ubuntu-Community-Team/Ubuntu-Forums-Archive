---
title: "Odd Partition Issue"
date: 2015-05-22
forum: General Help
---

### Post by Kit_Allen on 2015-05-22
Hi all (first post, woo!),
As a new Ubuntu user, I'm loving the experience so far. I've managed to set up a dual-boot system with Windows on my SSD for gaming, and Ubuntu on a small partition on my HDD for doing work. I've got the remaining space left over for general media that can be shared by both operating systems.

My media partition is NTFS, and can be recognised by both OSs pretty well. I say pretty well because there's no issue with Windows using it, but whenever I boot into Ubuntu, I have a slight problem.

It appears as though Ubuntu doesn't recognise the partition (or maybe just the files within) until I open Files and click on the Media partition. After doing so, the programs relying on files within are able to recognise said files. To help clarify, I'll list some exampled below:
[LIST]
[*]After booting into Ubuntu, if the first thing I do is open Rhythmbox, it cannot find any of my music and is just blank. The music files are stored in the Media partition.
[*]When booting into Ubuntu, my background is never loaded. To get my background, I must open Files, click on the Media partition (as outlined above), then open up System Settings/Appearance. This then loads my background.
[*]Other similar issues exist with all programs relying on the Media partition, which all have the same fix; open Files, click on the Media partition.
[/LIST]

Although this is a slight inconvenience, it is an inconvenience nonetheless. I'm aware that I'll likely need to provide more information if I'm to get help with this issue, but wasn't sure what info was necessary and what was not, so ask away and I will provide!
As this is my first post, I'm not sure if I put it in the right forum category. I apologise if it should be somewhere else.
Thanks,
Kit

---

### Post by Vladlenin5000 on 2015-05-22
Hi and welcome.

Additional drives aren't mounted by default. It all boils down to this, no need for that lenghty explanation ;) 
There are many ways to have them mounted automatically but I think you want something simple and graphical, don't you? Probably the easiest way is to open a tool called Disks. Then select the drive containing the partition you want mounted in the left and, on the right side click to select the said partition (you want to select your data partition only; your Windows system partition shouldn't be mounted, automatically or otherwise, because writing to it can render your Windows unbootable). Now that you have the correct partition selected, clcik on the double cog wheels and choose "Edit mount points" (or something similar, my system isn't in English). Next, all you have to do is toggle the switch an tick the first option. OK, reboot and test.

---

### Post by sotiris2 on 2015-05-22
That is because it is not mounted. Mounting (in brief non technical detail) means assigning a path to the partition kinda like windows assigns letters to partitions. Only Linux does not use letters but folders. Meaning you create a directory like MyDisk and you mount the partition to it. From that point on you access files on that partition as if they were actual files inside that directory. 

Nautilus (Files) explicity mounts the partition when you click on it and then browses to it automatically. Rhythmbox doesn't, it just tries to access the files. To make this work you need to mount a partition permanently (as in tell the system to mount it automatically at startup at a certain directory). 

A pre-installed (I think)utility called Disks can do that for you. First create a directory via Files, right click on it and copy it's location.Then run the Disks utility. Find your partition, select it and click on the 2-gears icon below. Select edit mount options, toggle automatic to off and make sure mount at startup is checked. Delete anything in mount point and paste the location you copied before. You need to add /name where name is whatever you named your directory (CaPiTaLiZaTiOn matters!!!!). Click ok. 

Now on reboot your partition will be mounted on that folder. You will need to tell Rhythmbox to scan there for songs. Before that you 'll probably want Rhythmbox to forget the old locations (as it will keep the old locations for the songs and complain when it doesn't find em.) To do that open Files in your home directory, hit Ctrl+H to show hidden files and go to folder .local/share/rhythmbox/   Once there delete the file rhythmdb.xml

---

### Post by Kit_Allen on 2015-05-22
Thanks for the quick replies guys, very helpful!
I thought I mounted my drive in Ubuntu when I set this machine up, but in Disks, it says "NTFS - Not mounted" until I click on it in Nautilus.

> **sotiris2 said:**
> First create a directory via Files, right click on it and copy it's location.

Very amateur question here, but where's a good location to mount it? '/media' ? (where '/' is the sort of base directory, yes?)

EDIT: Better yet, is it possible to mount it at '/'?

---

### Post by Kit_Allen on 2015-05-22
Okay so I did a really bad thing. Because I'm impatient, I mounted it straight to '/', which seems to be a major problem. Now when booting Ubuntu, I get a screen asking me to either press S to skip, or M to manually edit. Pressing S causes nothing to load, and pressing M I get a terminal-looking screen. Any ideas how to manually change the mount location?

EDIT: Fixed this issue, and mounted it at /media/*username*/MediaDrive , and everything is working well now! Thank you for your help guys :)

---

