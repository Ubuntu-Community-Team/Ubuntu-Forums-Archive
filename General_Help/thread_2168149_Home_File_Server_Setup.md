---
title: "Home File Server Setup"
date: 2013-08-16
forum: General Help
---

### Post by grandpavic on 2013-08-16
I have an older computer that is a dual boot Windows XP and Ubuntu 12.04. The machine has 2gb of memory and a 1.8 Hz Pentium 4 processor. In addition its has 3 hard drives for a total of about 1 Tb of disk.

I would like to lose Windows XP and turn the machine into a home file server. So the question is how do I proceed. 

Thanks for your help.

---

### Post by papibe on 2013-08-16
Hi grandpavic.

A few thoughts:
[LIST]
[*]All services can be set up on a Desktop or Server edition, then It's a matter of:
[LIST]
[*][*]personal preferences regarding how comfortable do you feel using the terminal; and 
[*][*]the resources you have, since the Dekstop will use more RAM, and a bit more processor time (not a problem in this case).
[/LIST]
[*]To wipe XP off:
[LIST]
[*]Install gparted, and reformat your XP partition to ext4.
[*]Make a permanent mount of the new partition on /etc/fstab.
[*]Upgrade grub.
[/LIST]
[*]Once XP is out of the picture, you can either:
[LIST]
[*]Keep your 12.04 as is, and provide services to the home network, or
[*]Remove/disable the GUI so it boots into text mode (to save resources).
[/LIST]
[*]Another solution would be to back up your data and do a clean reinstall either the desktop or server edition (both XP and the current Ubuntu version would be wipe off).
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by Lars Noodén on 2013-08-16
If you install the server edition of Ubuntu, it will give you a bare-bones set up.  The only thing you really need to get started would be to install the package openssh-server on it.  That will do two things.  It will allow you to log in and administer the machine without the burden of a GUI.  It will also allow basic file sharing using SFTP using the client's FileZilla, Nautilus, Dolphin, SSHFS, etc.  That last one, SSHFS, allows the remote machine to be accessible as if it were a local folder.  All the SSH methods work equally well (and are secure) over the wild Internet as the do over the LAN.  

However, if you are doing LAN access only and want something a little more complicated you can try Samba.  I'd give SFTP a go first.

---

