---
title: "Change permissions on second hard drive"
date: 2018-01-09
forum: General Help
---

### Post by michellesp on 2018-01-09
Hi all,

In my laptop I have two hard drives: 1 SSD drive on which a dual boot linux and windows is installed and one normal second hard drive which is mounted in linux.
My problem is, that in linux the permissions for the second hard drive are always set to read only. I tried to change the permissions using:

sudo mount -o remount,rw /run/media/michelle/Data
sudo chmod ugo +wx /run/media/michelle/Data
sudo chmod -R +wx /run/media/michelle/Data

This only works if I restart the laptop first in windows and then in linux. So it doesn't work if I only restart in linux. If I restart my laptop again the permissions are again changed to read only.
Can anyone help me changing the permissions on my second hard drive permanently in linux? I read something about adding it in fstab, but I'm very new to linux and I'm not really sure how to do this. Currently I can't find any line in fstab for the second hard drive.

Thanks in advance.

Kind regards,
Michelle

---

### Post by oldfred on 2018-01-09
What format is Data partition? It sounds like it may be NTFS?
And NTFS is not a Linux format, so does not support Linux ownership & permissions. You get the default ownership & permissions when you mount it.

And Windows may be turning fast start up or its  always on hibernation on with updates, so then the Linux NTFS driver only mounts read only.

Post this:
 sudo blkid -c /dev/null -o list 
and
cat /etc/fstab


 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

