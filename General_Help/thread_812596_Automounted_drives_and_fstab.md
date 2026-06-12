---
title: "Automounted drives and fstab"
date: 2008-05-30
forum: General Help
---

### Post by Tedward on 2008-05-30
After reinstalling Ubuntu 8.04 a couple times I have become familiar with how to mount hard drives and such using /etc/fstab, but why is it that when I install a fresh copy of 8.04 it automounts my other hard drives I have but they do not appear in my /etc/fstab?

I also like the feature that it has that lets me select the computer and all of the drives i have connected are in it.  However, after I mount the drives in /media/(hd_name) it no longer appears in the computer menu.  I'm sorry if that's not being descriptive enough, but if anyone could at least answer how my drives are mounted and working so easily without actually being in the fstab it would be greatly appreciated.

---

### Post by Tedward on 2008-05-30
Bumpity... Does anyone out there know how these drives are mounted?

---

### Post by fjgaude on 2008-05-30
I'm certainly no expert in the way Ubuntu is setup but the things you mention have something to do with the way gnome and .gvfs has worked to let terminal and Nautilus know what is there, and it has nothing to do with fstab. Even /etc/mtab doesn't show available mountable devices.

Just click on a device in Nautilus and an icon shows on the desktop; the device is mounted. Now click on the icon and you have your device filesystem.

Things like this have been changing from release to release. We get used to it.

---

### Post by Bakon Jarser on 2008-05-30
To get ntfs drives auto mounted you can use ntfs configuration tool (not installed by default).  Open it when your drives are unmounted and it will give you the option to make them mount at startup.

---

### Post by Tedward on 2008-05-31
It's not that I don't know how to set up my drives to mount like that on start up, that's very easy to do using /etc/fstab.  The question is how is my computer automounting everything without any of it being in my fstab file?  I also want to change the name of the drives from 200g media to something else, but since they're not mounted through fstab I don't know how to edit it how it is.

I like how it is set up now because i can click the computer icon that displays in my places menu and it actually shows all the drives.  When I set them up through fstab they don't appear here, and that computer icon becomes unusable.  I'm wondering how to edit it just how it is so I don't lose that feature.

---

### Post by fjgaude on 2008-05-31
Gosh, I'm somewhat at a loss... you can give each drive partition a label and that will likely be used when an icon for the partition shows:

```
sudo e2label /dev/sdx[n] <name>
```

How the computer automounts I can't say. So many options are shown in the System Tools/Configuration Editor in Gnome menus... you might slowly go through these and see if something helps, e.g., apps/nautilus/desktop and so on... much to learn, eh?

I can't remember if Configuration Editor is installed by default or if you have to get it from the repository. It might be called "gconfig", can't remember.

---

### Post by Bakon Jarser on 2008-05-31
I guess I really don't understand your problem.  I used ntfs configuration tool.  It lets you pick the mount point.  I chose /media/Cheeselog.  I click computer and it shows up there as Cheeselog.  If this isn't what your trying to do then could you explain it more clearly?

---

### Post by Tedward on 2008-06-01
I just recently reinstalled Ubuntu 8.04 and when I did all my drives were already mounted and I didn't have to do anything to them.  I'm just wondering where I can configure how it is mounted and such, it doesn't appear in my /etc/fstab so I can't just rename them without unmounting them and changing the name of the folder it is mounted to.  I did that the last time I installed 8.04 and it ended up taking the drive out of the computer section of my file browser.  I also can't have a name with spaces using fstab, they must have underscores. 

I guess what I'm really trying to ask is how to change the name of the mounted drive without changing where it is mounted to.  Right now it is mounted to the folder /media/disk but it is labeled 200GB Media.  How can I just change its name?

---

### Post by Tedward on 2008-06-01
NM figured it out from a different post :P

---

