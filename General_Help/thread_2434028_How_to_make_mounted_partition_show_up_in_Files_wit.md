---
title: "How to make mounted partition show up in Files with other partitions."
date: 2019-12-29
forum: General Help
---

### Post by jgwphd on 2019-12-29
This is probably a Nautilus question (or called files 3.34.1-stable). I am using 19.10 with an SSD and an HDD. The SSD has the Ubuntu OS. The HDD is shared with a windows 10 OS on the system. In windows I freed the space on the HDD for a new Ubuntu partition. Then in Ubuntu I created an Ubuntu partition using the free space on the HDD with "gparted" and mounted it using "disks" by checking "mount at system startup". The new partition is called Data-ubuntu. When I boot Ubuntu, the Data-Ubuntu partition shows up on the Ubuntu dock and in Files only if I click "other locations". How do I get the new Data-Ubuntu partition to show up in Files on the left sidebar, for example: the same way you see an external hard drive or USB stick plugged into a USB port. Or is this the way nautilus works? ...or are there better ways to get a convenient view of, or access to, all Ubuntu system storage. Thanks for any assistance or suggestions.

---

### Post by deadflowr on 2019-12-29
Just bookmark it.
When you navigate to the folder/partiton you want to have it'll show the name with an arrow in the window title bar, 
click on that and it'll give you a selection of options including Add to Bookmarks.


Edit: FWIW, bookmarks assumes the location is already mounted.

So if you bookmark the location but later on unmount that location, the bookmark will remain, and trying to open it will just produce an error message.

Hope that make sense.

Older versions of Files (which I don't think are supported by Ubuntu anymore) and other file managers for other Ubuntu Flavor desktops
(such as Kubuntu and Xubuntu) have the ability to mount partitions directly from the sidebar.
(Or at least they did)

---

### Post by jgwphd on 2019-12-29
Ok, Thanks. That works! but then I noticed that I had the option to rename it to what I want instead using the system name. Many Thanks!

...and thanks for the possible error heads-up ...so I don't get confused

---

### Post by Impavidus on 2019-12-30
I don't use disks. It's just another step and point of failure between giving user input and changing a config file. Instead, I modify /etc/fstab in a text editor. That way, I can mount any partition I want at any directory at boot time. I think your can use the file manager to bookmark locations.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

