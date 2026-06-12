---
title: "Help with home folder"
date: 2006-12-10
forum: General Help
---

### Post by simoncoul on 2006-12-10
Hi, I'm about to hook up a new hard drive, and I'm going to do a fresh install with 6.10.   I want to dual boot on the drive I currently have and use the second one to mount as my home folder.   In 6.10 does it still allow you to pick a drive/partition as your home folder.

Lastly, when I do another install for like 7.04 later next year can I simply install 7.04 and then say to mount this new drive as my home folder again and all my files will be there or does it overwrite things?

Thanks for the help.

---

### Post by 23meg on 2006-12-10
> In 6.10 does it still allow you to pick a drive/partition as your home folder.Yes.
> 
Lastly, when I do another install for like 7.04 later next year can I simply install 7.04 and then say to mount this new drive as my home folder again and all my files will be there or does it overwrite things?If you make a separate home partition, you can mount it later on.

---

### Post by ciscosurfer on 2006-12-10
I believe the Alternate install CD is what you want to use in order to specify a /home partition.

[LIST=1]
[*] This page will help you out as well (if you're already installed, this will help: [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)
[*]If you want to make a separate /home partition, and you about to install, then this page will help: [http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)
[*]If you want to know more about partitioning, then this page will help: [http://psychocats.net/ubuntu/partitioning.html](http://psychocats.net/ubuntu/partitioning.html)[/LIST]

---

### Post by 23meg on 2006-12-10
[QUOTE=ciscosurfer]I believe the Alternate install CD is what you want to use in order to specify a /home partition.[/QUOTE]No, you can with the desktop install as well.

---

### Post by ciscosurfer on 2006-12-10
> **23meg said:**
> No, you can with the desktop install as well.By setting up a new partition through Ubiquity (using gparted) during the install?  I suppose that makes sense.

Sometimes keeping the live/install, desktop, and alternate versions all straight can be difficult :-)

---

### Post by simoncoul on 2006-12-10
Ok so I will have install ubuntu and windows on one drive and use the second drive as my home partition.   Now the second drive will have all my files(like music and stuff) can I just say during the install process to mount the second drive as my /home, and then all my files will be in my home folder when I log in, or will they be on the same drive but not in the home folder?

Thanks for the quick responses

---

### Post by 23meg on 2006-12-10
> **ciscosurfer said:**
> By setting up a new partition through Ubiquity (using gparted) during the install?  I suppose that makes sense.No, the mount dialog should let you pick a partition you previously created as your home partition.

[IMG]http://debuntu.free.fr/images/Espresso/Screenshot9.png[/IMG]

---

### Post by ciscosurfer on 2006-12-10
@23meg,

Thanks for the info!  I assumed this was were to do it--of course, you need to actually have a partition or space available already, and using gparted (the partitioner used in Ubiquity) is the way to do it.

---

### Post by 23meg on 2006-12-10
[QUOTE=simoncoul]can I just say during the install process to mount the second drive as my /home[/QUOTE]Only if it's a Linux partition.

---

### Post by simoncoul on 2006-12-10
ok so when I install the drive, format it as ext3 transfer all my files to it.  During the install say to mount the drive as my home partition and then all my files will be there when I log in?   I'm just worried that when I mount it as my /home it will erase everything.   As long as the format thing is unchecked all the files will end up in the /home directory?

Thanks

---

### Post by 23meg on 2006-12-10
Yes. As long as you don't reformat it you should be fine.

---

### Post by simoncoul on 2006-12-10
Thank you for all the help!

---

### Post by 23meg on 2006-12-10
You're welcome; let us know how it went.

---

