---
title: "sudo disks-admin : command not found"
date: 2006-10-13
forum: General Help
---

### Post by Robban59 on 2006-10-13
Hi there,

it seems my Edgy beta installation is lacking Disks Manager : in System -> Administration I don't have any "Disks" item, and issuing the command "sudo disks-admin" I get  command not found.

Where is it hiding ? or how do I install it with Synaptic , how is the package called ?
Couldn't find anything with disk admin .

Thanks

---

### Post by Eran on 2006-10-13
I have exactly the same problem. Upgraded from Dapper to Edgy yesterday and now I have noticed that this is actually missing. From a quick search I have realized that it was intentionally taken out. Why?

---

### Post by jdusablon on 2006-10-17
Same here. I'm not familiar with the "parted" command, and I like that the disks utility showed the /dev identifier so I could quickly mount the drive and change my fstab.

Can I install this utility??

---

### Post by Mark Stosberg on 2006-10-31
Here's the [record of the meeting where it discussed that disks-admin being removed]("https://wiki.ubuntu.com/MeetingLogs/UbuntuDev_2006-05-11?highlight=%28disks-admin%29"). I experienced a bug with it myself. 

However, this should be documented in the release notes, along with a recommended alternative. Personally, I used the console-based "cfdisk", which I found installed by default. 

It worked OK for the partitioning job I had, although I had to hunt around that I needed to select "FAT32" to create a VFAT partition.

---

### Post by ayoli on 2006-10-31
disks-admin has been removed from gnome 2.16.
instaed you can use:
[LIST]
[*]baobab: for disks usage monitoring
[*]pysdm: as storage device manager
[*]gparted: as graphical partition manager
[/LIST]
there are all installable via synaptic/aptitude/apt-get

---

### Post by mongrol on 2006-11-01
I see they haven't updated the help files. It still has the Disks command it and even tries to tell you how to run it, only to find it doesn't exist.

---

