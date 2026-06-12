---
title: "connecting with XRDP and can't mount any drives"
date: 2014-06-22
forum: General Help
---

### Post by nowhere99 on 2014-06-22
Hi, I have just upgraded to a 14.04 Ubuntu desktop system and of course the gnome-fallback,flashback, classic whatever has to be broken so I had to install the LXDE for it's 2-D so I can continue to use RDP as I have with my 13.04 system. However, I cannot use any of the file managers to mount any drives (USB, SATA, nothing), that aren't already mounted in the fstab. I'm betting this is due to some remote permissions security thing but I can't figure it out. My user is part of the fuse group and I did the advanced privileges and made sure I have the allow mount/umount box checked and I've rebooted a few time since doing that. 

It used to work fine when I could use the 2D gnome in 13.04. How do I fix it?

Oh yeah, I can mount fine using any file manager from the console, just not through xrdp.


Thanks!

---

### Post by TheFu on 2014-06-22
Ubuntu (maybe Linux) has decided to protect us from ourselves. The intent is to prevent security issues on multiuser systems by allowing a remote user to screw around with mounts that someone sitting on the console has.  Console users are placed into local groups that remote users are not.

So ... what does all this mean to you?  Well, login on the console and capture the groups you are a member of - use "id".
Then remote in and do that again. Compare the two outputs.  What is missing? Manually add your userid to those other groups.
That should fix it.

BTW, allowing normal users to mount anything is just ... er ... SCARY! There are many ways to screw with a system through mount controls. Clearly, I am NOT a fan of the automatic mounting of USB or other drives.

---

### Post by nowhere99 on 2014-06-22
Thanks Fu! You had me excited there for a moment but unfortunately, the group list is identical when I log in using xrdp and directly on the console. Another interesting note is that I cannot log out when logged in through xrdp. Chosing logout simply drops me back on the desktop and I can't find any evidence I even tried to log out in any logs. When I log in on console, the two partitions on my USB drive are automatically mounted. Remotely I can unmount them by clicking the eject button but I can't remount them. The syslog shows the mounting and unmounting but nothing is logged about the "not authorized" failed attempt. 

Once I mount the USB drive from the command line (which I can do remotely) I am able to use programs like gencfs to mount encrypted folders without root priv even ones located on the USB drive. 

Thanks again Fu! Any other ideas?

---

### Post by nowhere99 on 2014-07-12
Does anyone have any other ideas? I can mount and unmount USB drives using nautilus simply by clicking on them when I am sitting at the computer but when I use remote desktop I cannot. This is a change from 13.04 because I did it all the time. Now in 14.04 If someone decided to protect me from myself I want to know how so I can undo it. It's my system. I'm the only user so I should be able to mount anything I want. Please let me know how they have denied this permission so I can undo it. polkit? fstab? 

Thanks!

---

### Post by nowhere99 on 2014-07-12
This also means I can't mount my encrypted folders using Gnome EncFS Manager gui...

---

### Post by TheFu on 2014-07-13
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB) section on user permissions ...> 
User Privileges
If your usb device doesn't appear on your desktop, you should check that your user has the correct privileges. Go to System->Administration->User and Groups, choose the user, click on "Properties", then go to the "User Privileges" tab. You should have the "Access external storage devices automatically" option checked. 

There is also **pmount** and/or adding your userid to the disk and plugdev groups which might help.

I did find a few other blogs that claimed the issue started with 13.10 and using GDM.  I'm confused how a login manager would matter for this at all, but I'm easily confused. ;)

---

