---
title: "Can not mount partition to fix corrupt file"
date: 2007-02-15
forum: General Help
---

### Post by jlr4u on 2007-02-15
I locked up my ubuntu by editing etc/X11/xorg.conf and put comments in the wrong section.
Now I can not reboot.
I poped in the live Ubuntu CD and thought If I could mount the partition, I would be able to edit the file and fix it.
Here is what I did.
First List the Partitions.
```
sudo fdisk -l

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10199    81923436   83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda3           10200       38536   227616952+  83  Linux
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris
```
Next Make a directory and mount the partition
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda3 /mnt/ubuntu
```
Navigate to the new partition and list files.
```
cd  /mnt/ubuntu
ls
[COLOR="Blue"]**lost+found**[/COLOR]
```


Can someone tell me what I am doing wrong to access my partition?
I get a [COLOR="Blue"]**lost+found**[/COLOR]

---

### Post by n00bish on 2007-02-15
Have you tried mounting /dev/sda1 instead of /dev/sda3?  I would think that sda1 would be the root partition.  Try mounting that and see what happens, if nothing does you should probably run fsck

---

### Post by crane on 2007-02-15
You may need to sudo ls. If you mounted it as root, you may not be able to access it as a user.
Also, You said you screwed up the xorg file. Does it crash to console when you try to boot?
If so just log in as user and edit the file there.
$sudo vi /etc/X11/xorg.conf

you can scroll down the file and delete what you need to. If you need to type something just go to where the text needs to be entered and hit I (for insert) then type what you need. Hit Esc when done to move around some more.
Then hit ESC
Type :
<SHIFT> ZZ to save and close the file.
If you mess up you can type:
:q! to close without saving.

---

### Post by n00bish on 2007-02-15
> **crane said:**
> You may need to sudo ls. If you mounted it as root, you may not be able to access it as a user.
Also, You said you screwed up the xorg file. Does it crash to console when you try to boot?
If so just log in as user and edit the file there.
$sudo vi /etc/X11/xorg.conf

you can scroll down the file and delete what you need to. If you need to type something just go to where the text needs to be entered and hit I (for insert) then type what you need. Hit Esc when done to move around some more.
Then hit ESC
Type :
<SHIFT> ZZ to save and close the file.
If you mess up you can type:
:q! to close without saving.

Unless he's familiar with vi/vim, I think nano would be a more user-friendly editor.

---

### Post by jlr4u on 2007-02-15
> **n00bish said:**
> Have you tried mounting /dev/sda1 instead of /dev/sda3?  I would think that sda1 would be the root partition.  Try mounting that and see what happens, if nothing does you should probably run fsck

Dah!!   Yes I knew better --- sda1 is the root and that fixed it 

Thank You!

---

