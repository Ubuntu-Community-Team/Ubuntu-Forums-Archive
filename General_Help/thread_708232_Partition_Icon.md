---
title: "Partition Icon"
date: 2008-02-26
forum: General Help
---

### Post by technotika on 2008-02-26
Hi Guys

I'm looking to get ICONS on's the desktop for my partitions.

During the install process I mounted a 40 gb disk prted as ext3 in a Folder Called BACKUP off the /file system

And Also mounted another DISK for DATA in the /home dir ext3 also.

Everthing is fine the back up drive is registered as stemming from the correct folder and so is home.

However Iwas wondering if there was a way to make them have icons on the desktop as well
as if they were just normal partitons. 

Thanks a lot in advance 

J-D:KS

---

### Post by imoatama on 2008-02-26
What version of ubuntu are you running? Usually gnome-volume-manager mounts the drives automatically, and nautilus will display them as icons on the desktop (at least for me).

Are the drives mounted already? Do they appear in the 'Places' menu?

---

### Post by technotika on 2008-02-26
Hi there thanks for taking time out and helping me.

It's 7.10 the latest from the website  - I think thats gutsey?

No the disk dont show In places and yes they are mounted.

If I take a look at gparted it says they are mounted (ie if I right click the optiion is there
to "un mount")

So they are definitley there and mounted I suspected its to with they are mounted.

From my learnings of the FSTAB file I can only assume all is looking ok there too since they mount at boot 
even though they dont show as disks just folders in the /file structure.

I mounted the Data drive in the HOME dir at install for redundancy  - ie if the system goosed I could
live cd or rescue cd and copy the data or just do the same install again and the home drive would hook up 
to the drive again leaving me all my data intact.

Thanks again!!!

---

### Post by NilsE on 2008-02-26
Go into the configuration editor and find the    apps > nautilus > desktop section and you can select volumes at the bottom of the right window.  If a device is mounted it will then show up on the desktop. There are a few things you can select in there to show on the desktop.

---

### Post by technotika on 2008-02-27
thanks - quite new and cant see what ur refering to  - how do I do that ?:popcorn:

---

### Post by NilsE on 2008-02-27
> **technotika said:**
> thanks - quite new and cant see what ur refering to  - how do I do that ?:popcorn:
If you go into the Applications menu under system tools there should be a selection for configuration editor.  If it is not there go into system > preferences > main menu and find it under system tools and select it.

Or you can go into a terminal and enter

gconf-editor

You can then look for the entires I mentioned above.

---

### Post by technotika on 2008-02-29
hi dude 

sorry not got back  - had some issues and am reinstalling  - during the install I did a manual partiton 
and mounted the drives as deva/BACKUP and the or   devb/DATA in the /media folder and that did the trick - just needed to set permissions with CHOWN and hunky dory now.!!!

---

