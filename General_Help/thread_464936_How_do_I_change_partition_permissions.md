---
title: "How do I change partition permissions?"
date: 2007-06-05
forum: General Help
---

### Post by skywatcher on 2007-06-05
Please excuse me if a similar topic has already been covered. I did some searching but couldn't find anything.

I have a dual-boot system (XP/Dapper), and when I start Linux, the Windows partition is automatically mounted as /media/hda2. This is great, because I can access files saved under Windows. Unfortunately, it is mounted with read-only permissions, so I cannot use that part of the HD to save data from Linux. I have tried to change the permissions, without success. Can anyone tell me how I can do this?

Thanks.

---

### Post by eggdeng on 2007-06-05
Presumably because your Windows partition is NTFS , so you need to do some work to make it writeable. Google for a tutorial or try [http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)

---

### Post by eentonig on 2007-06-05
Install ntfs-3g to allow write access to ntfs file systems.

In a terminal:
> sudo apt-get install ntfs-3g

And then under System\Administration or System\Preferences (I'm not sure), you have a new menu which allows you to activate the write access.

Make sure you properly shut down your pc when you're in windows. Because write access will fail if the disk isn't properly released in windows (ie. hibernation)

---

### Post by skywatcher on 2007-06-05
Thanks very much for the advice -- I got it right!

---

### Post by LoTech242 on 2007-06-05
I followed the guide, and it worked great for my harddrive. But when I tried the same thing with a portable hard drive it doesn't show up.... here is what my fstab looks like:

/dev/sda1   /media/sda1   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdb5   /media/sdb5   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdb6   /media/sdb6   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdb7   /media/sdb7   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdb8   /media/sdb8   ntfs-3g  defaults,locale=en_US.utf8    0    0

sdb5 through sdb8 is the portable harddrive.

does anyone have any ideas?

TIA

---

### Post by OttifantSir on 2007-06-11
I used Synaptic and searched for NTFS and got the ntfs-3g package. I thought that would be it. No luck. So, I tried the ntfs-config. I opened it under Programs -> System Tools (Might have to enable this menu under System -> Settings -> Main Menu)

I enabled read/write for all drives, internal and external. It wouldn't work at first because the drives were mounted, and to unmount, they had to be written to (quite a bad flaw IMHO). So, I restarted into Windows, disconnected the externals and rebooted into Ubuntu. Now, you may not have to reboot into Windows, but that's what I did because the program told me to.

See if this works for you.

---

