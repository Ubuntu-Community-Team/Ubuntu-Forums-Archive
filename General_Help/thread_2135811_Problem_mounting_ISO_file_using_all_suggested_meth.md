---
title: "Problem mounting ISO file using all suggested methods"
date: 2013-04-15
forum: General Help
---

### Post by Carmageddon on 2013-04-15
Hello guys, I have an iso file which is about 8.4GB, and mounts fine under Windows 8 using Daemon Tools on laptop - where I can see ALL files.

When I try to mount it from command line, like: 
mount -o loop /home/user/Downloads/StarCraft_II_Heart_of_the_Swarm-FLT/flt-hots.iso /mnt/iso/
mount -o loop -t udf /home/user/Downloads/StarCraft_II_Heart_of_the_Swarm-FLT/flt-hots.iso /mnt/iso/

I get it mounted with only one directory and one file...
When I tried to use suggested tools such as AcetoneISO, I get error:
> Error, could not mount image.

Solution:
Try converting the image to ISO or extract the content to a folder from the upper menu "Image Conversion."
NOTE: it is NOT possible to mount multi-sector images.
For more information, please visit official website: [http://www.acetoneteam.org](http://www.acetoneteam.org)
(The site is inactive so no info there).

My google searches on the subject and looking for similar threads on ubuntu forums turned on relevant solutions :(


Please, help me... I wanna keep to minimum the amount of things which DONT work for me on Linux (VPN to work is one I accepted, but I wont accept inability to mount ISO files...).

Oh, and I am on Ubuntu 13.04 Raring Ringtail, 64 bit.

---

### Post by Carmageddon on 2013-04-16
ok I found out the source of my problem!!
The mount command (as is AcetoneISO) ALWAYS mount as root-only, except one directory and one executable file which are visible to normal user.
This is why when I always mounted as root, then checked as normal user, I only saw 2 files mounted.
Once I started checking with root - I saw all files are actually mounted!

I found out that it mounts properly only through nautilus, but I cant find a CMD line which works the same - this guide is wrong [https://help.ubuntu.com/community/MountIso#From_the_Command_Line_.28As_a_Regular_User.29](https://help.ubuntu.com/community/MountIso#From_the_Command_Line_.28As_a_Regular_User.29)

Any ideas?

---

### Post by Carmageddon on 2013-04-16
ok I found out the source of my problem!!
The mount command (as is AcetoneISO) ALWAYS mount as root-only, except one directory and one executable file which are visible to normal user.
This is why when I always mounted as root, then checked as normal user, I only saw 2 files mounted.
Once I started checking with root - I saw all files are actually mounted!

I found out that it mounts properly only through nautilus, but I cant find a CMD line which works the same - this guide is wrong [https://help.ubuntu.com/community/MountIso#From_the_Command_Line_.28As_a_Regular_User.29](https://help.ubuntu.com/community/MountIso#From_the_Command_Line_.28As_a_Regular_User.29)

Any ideas?

---

