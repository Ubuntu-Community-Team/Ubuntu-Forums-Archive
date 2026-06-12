---
title: "Thunar sidebar."
date: 2007-08-09
forum: General Help
---

### Post by Freddy on 2007-08-09
Hi all.
I just reinstalled Ubuntus base system with Enlightenment17 and removed my Windows operating system, I installed Thunar for some graphical filemanagement. 

Now to my problem :).

When I "named" my partitions within "disk management" inside Win XP, Thunar picked up their name and used them inside the sidebar, but now when I have formated all of my disks (and cant use XP to name them :)) Thunar uses names like, 117G Volume, 199G Volume. How can I rename those disks to the proper mounted name?

They are both mounted as Storage1 and Storage2 inside /media.

/Freddy

---

### Post by apetresc on 2007-08-09
You have to give them a volume label. This is easily done with the e2label utility.
```
man e2label
```

This assumes they are ext3 or ext2. If they are not, post what they are and I can give instructions for those too :)

---

### Post by merlinus on 2007-08-09
Did not work for me in Thunar since the partition (ext3) already has a volume label.  It shows up correctly in Nautilus, however.

-merlin

---

### Post by Freddy on 2007-08-09
> **AdrianP said:**
> You have to give them a volume label. This is easily done with the e2label utility.
```
man e2label
```

This assumes they are ext3 or ext2. If they are not, post what they are and I can give instructions for those too :)
Thanks for helping but what should I actually write? 

I tried to use:
```
e2label 117G Volume Storage1
```
and e2label answered 
```
Usage: e2label device [new label]
```
but everything looks the same in Thunar, I use ext3 on my partitions.

/Freddy

---

### Post by apetresc on 2007-08-09
The first parameter to label has to be a device name, like "hda1" or "sda2". You can see what this should be by examining the output of "mount".

So if your 117GB hard drive was "/dev/sda2" then you would type ```
sudo e2label /dev/sda2 MyNewName
```

---

### Post by Freddy on 2007-08-09
> **AdrianP said:**
> The first parameter to label has to be a device name, like "hda1" or "sda2". You can see what this should be by examining the output of "mount".

So if your 117GB hard drive was "/dev/sda2" then you would type ```
sudo e2label /dev/sda2 MyNewName
```
Thanks man, I got them named now. Looks so much cleaner :).

---

### Post by jminker on 2008-01-25
> **AdrianP said:**
> You have to give them a volume label. This is easily done with the e2label utility.
```
man e2label
```

This assumes they are ext3 or ext2. If they are not, post what they are and I can give instructions for those too :)

I am using Thunar as well, except that I use reiserfs. How would I change the volume names for that? Thanks, Jim :)

Okay, I found the solution:
[reiserfstune]("https://help.ubuntu.com/community/RenameUSBDrive")

---

