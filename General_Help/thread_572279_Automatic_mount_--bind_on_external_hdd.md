---
title: "Automatic mount --bind on external hdd"
date: 2007-10-10
forum: General Help
---

### Post by mozjonathan on 2007-10-10
Hi,

My external hard drive has two partitions : Name1 is FAT32 and Name2 is ext3. They both usually get mounted as /media/Name1 and /media/Name2.

I have in my home a folder named Folder1 which I mount --bind /media/Name2/Folder1 /home/jonathan/Folder1 so that the contents of Folder1 on my external hdd are available from my home directory. 

How can I do that automatically ? If I add the proper line in /etc/fstab (line is : /media/Name2/Folder1 /home/jonathan/Folder1 none bind) hal seems to be unable to mount the external hard drive.

Has anyone ever succeeded in doing such a thing ?

Thanks in advance.

Jonathan

Edit : I forgot to mention that making a symlink isn't what I'm looking for :)

---

### Post by thirddeep on 2007-10-10
Search this forum for UDEV, that should help you :-)

Thd.

---

### Post by mozjonathan on 2007-10-10
Yes, I've seen that [http://ubuntuforums.org/showthread.php?t=378663&highlight=udev+bind+mount](http://ubuntuforums.org/showthread.php?t=378663&highlight=udev+bind+mount) for instance but writing as the man says the rule in /etc/fstab gives me an "Unable to mount volume Name2". Do you think I should try to write an udev rule to add the additionnal mount command for the partition whose uuid is the one I'm looking for ?

---

### Post by mozjonathan on 2007-10-10
Just a small bump to ask if anyone would know how to write such a rule ? I didn't manage to find the proper file telling udev how to mount cdroms.

---

### Post by mozjonathan on 2007-10-11
I was thinking : the best would be just to tell hal to run a script of my own when it automounts my device. Couldn't set this up using gnome-device-manager - only available for usb mouses. Does anyone know the configuration file that would allow me to specify a script to be run in case a specific device gets mounted ?

---

### Post by vanadium on 2007-10-11
Unix and Linux have a very simple mechanism to allow you to organize the data the way you want, and that is: symbolic links. Just put a symbolic link pointing to your harddrive in your home dir and you'll be all set in a safe and foolproof manner.

---

