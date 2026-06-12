---
title: "Ubuntu can't find files with special character names"
date: 2008-05-16
forum: General Help
---

### Post by Ionna on 2008-05-16
Background: I downloaded some music (before using ubuntu) that for one reason or another, did not get translated very well into normal alphabets. Instead, they come out with characters such as: #$%^&* etc. Winamp plays these MP3s fine, but not Amorak. 

Without going into ubuntu itself and actually renaming each individual file, is there a way I can get Ubuntu to recognise the files? Thanks!

Edit: The fonts are something like this: ¥Ê¥¤¥È¥á¥¢

---

### Post by DieB on 2008-05-16
What I did (i had a similar problem a year ago) was changing the encoding to utf8 via utf8-migration-tool (it is inside the universe repository of ubuntu)

hope that helps

---

### Post by Ionna on 2008-05-17
Ah, thanks! Will try that!

---

### Post by Ionna on 2008-05-19
Well, the tool seems to work, but the files that I need to be renamed are in my host folder, while the rename only seems to work for the home folder. Is there a way for me to get it to rename host instead?

---

### Post by DieB on 2008-05-19
what host folder?

is it on a separate disk?

---

### Post by Ionna on 2008-05-20
Nope, it's on a different partition. 

Home = Ubuntu

Host = Windows

---

### Post by DieB on 2008-05-21
okay as far as I assume you have videos and/or music on your windows partition and you access them from ubuntu, right?

so mounting the whole windows partition into your ubuntu /home/YOU/win(or what ever) might not be helpful - cause it might happen, that registry or something other granular might break, although MS claims to support utf8.

So i would suggest to make a third partition formatted in VFAT/FAT32 that holds all data that needs to be accessed by both systems. This will apear in windows as d: or what ever and in ubuntu you might be able to mount it on whatever place you want (means: also inside of the home directory).

[For questions to the Linux filsystem hirarchy see:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

to perform the operation mentioned above do the following:

**1) defrag windows partition and backup files**
u should defrag several times so all data is sitting on the beginning of the partition - otherwise you might lose data on later steps.
then copy all that data that should get to the new partition onto the ubuntu or if there is not enough space, use an external disk
(I heard some folks buy disks and give/bring it back afterwards, if they not have enough spare space)
[B]
2) install gparted[/B]
use apt-get install, add/remove or synaptic

**3) unmount the windows partition**
do it via the icon on the desktop, or perform: 

> sudo umount [mountpoint of the win partition]

to get the mount point you can type mount in a terminal and it will list you all mounted partitions with some extra info

**4) perform the resize of the win partition**
start gparted, under gnome you find it under System it is named Partition Editor, otherwise type following in a terminal:
> sudo gparted
now you will see your partitions in a chart diagram. to resize the windows partition right click on it and select resize (don't forget to get enough space, so you needn't to perform these steps soon again). Apply for your changes.

**5) create the new partition **
if everything went fine, right click on the greyed out area and select "new" and partition it as fat32. done this once again apply.

**6) create new mount point for new partition and mount it **

creat a folder inside your home, that will later be use to mount your data in. i used media. (mkdir /home/YOU/media would do the trick in the terminal)

so now edit fstab:
> sudo gedit /etc/fstab
you might see some entries, that could be used as examples, but u could just paste the following at the end of the document:
> sda3   /home/YOU/media   vfat   relatime    0    0
**and change** sda3 to the apropiate (you can check this inside gparted), dont forget to replace YOU also.

This done save that file and restart your computer.
Now copy the data that was backed up in your folder "media" (or whatever you named the folder). It is now on the new partition. To check if it worked simply boot into windows search for the new letter and check.

Done all that you can run utf8-migration-tool on the data and amarok should play your files.

Well that looks pretty much, but is worth it.
Hope it helps.

---

### Post by Ionna on 2008-05-22
Sorry for the late reply!

Noted and Noted! I'll try these when I get my external back. Thank you!

---

### Post by Ionna on 2008-05-23
First post updated with actual mp3 tag. The file name itself is actually a question mark, so I'm not sure whether it's because of the language file or encoding.

---

