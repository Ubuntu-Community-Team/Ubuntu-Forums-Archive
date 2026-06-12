---
title: "Update manager won't run after a recent update following restore"
date: 2017-06-07
forum: General Help
---

### Post by david_williams on 2017-06-07
After a recent update, update-manger would not run. I had a problem just like the one mentioned in [https://ubuntuforums.org/showthread.php?t=2295608](https://ubuntuforums.org/showthread.php?t=2295608)

At least that provided the answer to get me running again.
/usr/lib/dbus-1.0/dbus-daemon-launcher-helper was owned by "root:mlocate" instead of the correct "root:messagebus".
Plus, in my case, the SUID bit was not set, so I also had to "sudo chmod u+s" for that file.
Good thing I had another system to look at! 

But, a) I had recently restored my root directory from a backup (including the /etc directory). And, I have used 'update-manager' since then.
And b) after my restore, I have found some other cases where the 'permissions' and 'owners' were messed up.
I did the "restore", say to partition sda8 after booting up to a clean install from partition sda2 (and backups were on partition sdc1).

So, my questions:

Does anyone know how this could happen? That is, did I make a common newbee mistake in my restore? I use 'duplicity' to backup and restore and think it simply uses rsync under the covers. 

Second, is there any (relatively easy) way to check if all ownerships are now correct? Or, do I just have to wait until something breaks?
The fact that I had used update-manager after the restore, and then later had the problem, implies to me something else is not quite right. 

BTW, out of curiosity I checked, and the only other file owned by group mlocate is mlocate.db. /usr/bin/mlocate is owned group 'libvirtd' but apparently it should be 'mlocate'. 
A number of flies in /proc are owned by 'messagebus' group, but that's similar to my comparison system. 
The "UIDs" in my restored passwd file and group file are not the same as those on my comparison system -- I assume they are rarely the same-- but wonder if somehow during the restore the "shadow passwords" of the system I was restoring from came into play for the system I was restoring to, or something? 

Thanks for any advice,

---

