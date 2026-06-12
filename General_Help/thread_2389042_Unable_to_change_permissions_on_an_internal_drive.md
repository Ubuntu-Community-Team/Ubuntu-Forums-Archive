---
title: "Unable to change permissions on an internal drive"
date: 2018-04-10
forum: General Help
---

### Post by nickdc on 2018-04-10
Running Ubuntu-Gnome 16.04 on an elderly machine. I have a separate internal hard drive - Media - which I use for data storage. I'm moving to a new machine and want to copy key folders (Photos, Music, Videos etc) across to the new machine. I thought it would be simple to share those folders on the LAN and copy across. But I find I can't share them as they're owned by root. So I tried

```
sudo chown -R nick:nick /mnt/Media
```
 
There was a longish pause before the terminal prompt reappeared, and I assumed the permissions had been changed. But when I returned to the drive I found it was still owned by root and not being the owner I couldn't change the permissions. Same happened when I tried changing ownership of an individual folder on the drive.

I was offered a workaround for the sharing by editing the samba.conf file, but I'm curious to understand where I'm going wrong; I've not done much permission changing thus far.

---

### Post by yancek on 2018-04-10
So what operating system and version is on the new machine?
Are you copying from the old machine to the new machine?  Would work better the other way around.  Where are you copying them to on the new machine, what directory?  You mention Samba, are either the old or new partitions windows filesystems?  Linux ownership/permissions are meaningless on windows filesystems, you need to use umask.

---

### Post by nickdc on 2018-04-11
Thanks for responding, Yanek. I think you've identified the problem: the Media drive is ntfs, because it was originally shared with a Windows installation. I will investigate umask. Thanks.

---

