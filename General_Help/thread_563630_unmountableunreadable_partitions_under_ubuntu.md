---
title: "unmountable/unreadable partitions under ubuntu"
date: 2007-09-30
forum: General Help
---

### Post by banda on 2007-09-30
[IMG]http://i23.tinypic.com/1zdpw1c.jpg[/IMG]
thats how my partition table looks now.

i am running gutsy beta from the last couple of days. ihave all my data stored on hda2 and hda3 and have my windows install(which is no longer working) on hda5. till a few hours back i was able to access hda2&3 without any problem although hda5 has never been showing up in ubuntu. but somehow i can no longer access my main storage partitions now... have i lost the data?????
help

---

### Post by WakkaDojo on 2007-09-30
Don't worry, the data is still there!

Perhaps you can try to mount them with ntfs-3g. 
 *NOTE: In this example I am using the partition hda2 for mounting, though you can repeat this for any ntfs patition number.*
First, install it:
```
sudo apt-get install ntfs-3g
```
Next, make a directory to mount your partition. In this example we'll mount in the "/media" directory:
```
sudo mkdir /media/hda2
```
If the directory already exists, don't worry about it.
Now, mount the volume:
```
sudo mount -t ntfs-3g /dev/hda2 /media/hda2
```
I hope it works! I don't have any ntfs partitions to test it on right now, but good luck.

---

