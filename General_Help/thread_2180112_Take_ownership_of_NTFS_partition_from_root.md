---
title: "Take ownership of NTFS partition from root"
date: 2013-10-11
forum: General Help
---

### Post by huxley2 on 2013-10-11
Hi, everybody

I've been trying unsuccessfully, for the past couple of days to get ownership of my ntfs data partition and still no closer to getting my head around it. I've tried to change ownership via nautilus and various chown cmds in Terminal but nothing seems to work.

Here's what my fstab has to say about things - ntfs partition is /dev/sda2


```
#Entry for /dev/sda3 :
UUID=5da328cc-8250-41d3-91a2-02749384398c    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda2 :
UUID=64F04B09F04AE0C2 /media/aaron/Data auto nosuid,nodev,nofail,x-gvfs-show 0 0
#Entry for /dev/sda5 :
UUID=bb3fafc9-5ef6-4379-88fe-2431b8fc313b    none    swap    sw    0    0
```

Regards,

Huxley

---

### Post by nothingspecial on 2013-10-11
Hi, you're right in that you need to add a line to your fstab file. This post explains it in detail, there is a specific ntfs bit

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Any problems post back but it is worth having a good read of that post and the wiki page it links to so you understand what you're doing.

Also, always make a back up of your fstab before you mess with it (although if the worst comes to the worst I suppose you have a record of it in this thread)

---

### Post by oldfred on 2013-10-11
Some other links also.
 Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

I prefer this set of instructions as it has a couple of newer settings that you should include.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

      
 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

---

### Post by huxley2 on 2013-10-11
Thanks, Grim.

I'm still fairly new to linux / ubuntu so that thread - at 1st glance very daunting - will probably take me a day or so to get through. For good or ill, I'll post my results sometime over the weekend.

---

### Post by huxley2 on 2013-10-11
Thanks, Fred. I'm out for the night now so will get into all of that tomorrow.

---

### Post by huxley2 on 2013-10-12
O.k, well that was easier than I anticipated, I used your code, Fred and it's all sorted. 

Job done.

---

