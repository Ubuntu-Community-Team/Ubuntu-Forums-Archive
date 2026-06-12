---
title: "File manager slow to open (Xubuntu and Kubuntu 12.04 - Thunar, Dolphin, Krusader)"
date: 2013-12-03
forum: General Help
---

### Post by mstaszew on 2013-12-03
Hi there,


I'm running Xubuntu 12.04 and have an annoying problem where Thunar is slow to open at times. I've tried all of the suggestions I could find including setting AutoMount=false in both network.mount and smb.mount as well as setting Type=smb-server in smb-browse.mount and nothing is working. I've also installed Dolphin and it too is showing the slowness. The slowness is not present every time, only after a period of not using the file manager. I have 3 Windows shares mounted in /media and they are included as favorites on the left side of both Dolphin and Thunar. I've noticed that if I kill the file manager while it is "hung" and I execute a script I have to remount the Windows shares that the file manager loads quickly. What can I do to resolve or debug this issue?


I've been desperately trying to use Linux on my work machine, but I need to access the file system often and can't have these delays. I've also tried Ubuntu 12.04/13.10, but quickly gave up because of Unity and Gnome 3 wasn't any better. I've tried Kubuntu 12.04 as well and both Dolphin and Krusader showed similar problems.


Thanks in advance for any guidance.


Michael

---

### Post by mstaszew on 2013-12-03
I realized I never defined slow. By slow I mean minutes to open, sometimes 5 or more.

---

### Post by crono1412 on 2013-12-14
> **mstaszew said:**
> Hi there,


I'm running Xubuntu 12.04 and have an annoying problem where Thunar is slow to open at times. I've tried all of the suggestions I could find including setting AutoMount=false in both network.mount and smb.mount as well as setting Type=smb-server in smb-browse.mount and nothing is working. I've also installed Dolphin and it too is showing the slowness. The slowness is not present every time, only after a period of not using the file manager. I have 3 Windows shares mounted in /media and they are included as favorites on the left side of both Dolphin and Thunar. I've noticed that if I kill the file manager while it is "hung" and I execute a script I have to remount the Windows shares that the file manager loads quickly. What can I do to resolve or debug this issue?


I've been desperately trying to use Linux on my work machine, but I need to access the file system often and can't have these delays. I've also tried Ubuntu 12.04/13.10, but quickly gave up because of Unity and Gnome 3 wasn't any better. I've tried Kubuntu 12.04 as well and both Dolphin and Krusader showed similar problems.


Thanks in advance for any guidance.


Michael

I have the same problem, and it isn't just the file manager, its any dialog that needs to access a file open or save dialog.  Could you share the script you use to get things moving again as a work-around.  The only way I've been able to fix it is by restarting.

---

### Post by mstaszew on 2014-01-10
Hi there. I apologize for the severely delayed response. I thought I would have been notified automagically of new replies, but that was not so. Here is my script. Replace "myshare" "shared_resource" "username" and "password" with your values. I have 3 shares so I have these lines duplicated and adjusted for each. I execute the script as sudo. It's annoying to have to do this, but at least it eliminates the need to restart.

umount /media/myshare
mount -t cifs //shared_resource -o rw,username=username,password=password /media/myshare

---

### Post by crono1412 on 2014-01-10
Thanks, I actually figured out a more elegant solution, and that is to use Automount.  Automount polls specific folders for access, and when those folders are accessed, it mounts whatever share is supposed to be there.  After a timeout period, it unmounts those folders.  Since getting it configured, I haven't had the problem we describe in the thread.

The instructions for configuring it are kind of confusing, but its definitely the work around you want to use.

---

### Post by mstaszew on 2014-01-10
Most excellent. Thanks for the info. I'll be sure to run through the config docs sometime today.

---

### Post by mstaszew on 2014-01-10
autofs installed and configured without issue and I'm able to see my shares just fine. fstab edited to remove my shares from there and all appears fine. Thanks a bunch for pointing me to autofs.

---

