---
title: "Briniging the partitions to The Right Path"
date: 2006-12-21
forum: General Help
---

### Post by Homayoon on 2006-12-21
It is about a month or so that I have switched from Windows XP to Ubuntu 6.06. Perfectly satisfied and now more familiar with Linux, I'm going to make things a little bit more comfortable. The one thing that is bothering me is my hard drive's "layout", that is the way I have partitioned them. I like to change the my partitions, maybe a few merges/resizes/splits and then probably I would want Ubuntu to be on a different partition than it is and /home be on its own separate partition. I really don't like to reinstall everything, so I was wondering if I could do something else. I guess I should be able to boot to a live CD, rearrange the partitions the way I like, copy all Ubuntu directories, except /home, to the partition I want, then copy /home to a dedicated partition and arrange other things as I like. I suppose, the only thing that remains is fixing grub to load the system correctly. I'm not sure how I can do this last one, and a little mistake can cost me my life (that is my hard drive!). Can anyone kindly suggest some safe way to do this? And besides, are other things in the scenario correct? I appreciate any help.

---

### Post by bodhi.zazen on 2006-12-21
> **Homayoon said:**
> It is about a month or so that I have switched from Windows XP to Ubuntu 6.06. Perfectly satisfied and now more familiar with Linux, I'm going to make things a little bit more comfortable. The one thing that is bothering me is my hard drive's "layout", that is the way I have partitioned them. I like to change the my partitions, maybe a few merges/resizes/splits and then probably I would want Ubuntu to be on a different partition than it is and /home be on its own separate partition. I really don't like to reinstall everything, so I was wondering if I could do something else. I guess I should be able to boot to a live CD, rearrange the partitions the way I like, copy all Ubuntu directories, except /home, to the partition I want, then copy /home to a dedicated partition and arrange other things as I like. I suppose, the only thing that remains is fixing grub to load the system correctly. I'm not sure how I can do this last one, and a little mistake can cost me my life (that is my hard drive!). Can anyone kindly suggest some safe way to do this? And besides, are other things in the scenario correct? I appreciate any help.

Define "safe"

I advise you back up first.

See this site to list your creent packages in the event you end up deciding to re-install:

[http://duggmirror.com/linux_unix/Ubuntu_tricks_how_to_create_a_list_software_and_use_it_to_restore_your_pc/](http://duggmirror.com/linux_unix/Ubuntu_tricks_how_to_create_a_list_software_and_use_it_to_restore_your_pc/)


OK then. I would use GParted, but that is just me:

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

OK, now that we have partitioned, lets move home :)

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

HTH

8)

---

### Post by Homayoon on 2006-12-21
Thanks for your reply.

What about grub? Won't I need to fix it if I want to move Ubuntu to another partition?

---

### Post by bodhi.zazen on 2006-12-21
> **Homayoon said:**
> Thanks for your reply.

What about grub? Won't I need to fix it if I want to move Ubuntu to another partition?

You will need to edit /boot/grub/menu.1st  and /etc/fstab on your Ubuntu partition after you move them (root and home partitions). The UUID will change. You can list partitions by uuid with:```
ls /dev/disk/by-uuid -lh
```

I do this on the GParted CD.

See if this helps:

[http://www.ubuntuforums.org/showthread.php?&t=316237](http://www.ubuntuforums.org/showthread.php?&t=316237)

---

