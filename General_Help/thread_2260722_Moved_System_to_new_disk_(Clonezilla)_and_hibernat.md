---
title: "Moved System to new disk (Clonezilla) and hibernate quit"
date: 2015-01-14
forum: General Help
---

### Post by Ralph L on 2015-01-14
I just used Clonezilla to move my Ubuntu 12.04 system to a new and larger disk.  Everything works but hibernate.  Hibernate appears in the shutdown menu.  When I select hibernate the disk gets busy like it is writing the hibernate file.  However, when I restart, the system goes through the normal startup (longer than a hibernate restore) and doesn't restore the applications that were running at shutdown.  Hibernate has been enabled using the method given here:  [http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html](http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html) .  If I reinstall the old disk hibernate works, so something happened during the move of the OS partition to the new disk.  I did have to change the uuid of the swap partition with the move to the new disk, since the swap partition was moved from sda5 to sda3.  I did this by changing the uuid number in the /etc/fstab file to the uuid that gparted set up for the new sda3 swap partition.  If I turn swap on and off everything seems normal. ```
ralph@Lat1:~$ sudo swapoff -av
swapoff on /dev/sda3
ralph@Lat1:~$ sudo swapon -av
swapon on /dev/sda3
swapon: /dev/sda3: found swap signature: version 1, page-size 4, same byte order
swapon: /dev/sda3: pagesize=4096, swapsize=3559915520, devsize=3559915520
ralph@Lat1:~$
```

Anybody got any ideas how I could test this further to see what is wrong?

---

### Post by sudodus on 2015-01-14
I guess the problem is due to the change of partition (and UUID) of you swap.

- Maybe if you disable hibernation and then enable it again using that same method, you would get everything correctly set up and hibernation will work again.

- Alternatively change the UUID of the swap partition to what it was before. Please check that it is the correct partition, so that you do not overwrite valuable data !!!

```
sudo mkswap -U enter-the-original-UUID-string-here /dev/sda3
```

and change it in **/etc/fstab** too.

---

### Post by Ralph L on 2015-01-14
sudodus:  Thanks for responding. I tried your suggestion of disabling hibernation by the same method that I enabled it, and then re-enabling it.  Didn't work.  I then tried your second method using mkswap and changing /etc/fstab back to the original swap partition number.  It worked!!!  I could hibernate from my default boot partition (the one at the top of the boot list that I use most of the time).  Thank you.
But I still have problems.  I have 3 OS partitions on the disk.  1.  My main one--ubuntu 12.04, 2.  xubuntu 12.04, and 3.  ubuntu 14.04 (this one was just loaded and I hope to use it in the future, when I get it set up).  Anyway now I can't hibernate from the xubuntu partition (I haven't set up ubuntu 14.04 for hibernation yet).  Xubuntu uses the same swap partition as the other OS partitions (is this allowed?), but it is a different swap partition than it had previously used, before the cloning.  I tried your second suggestion on it (using mkswap to set it to the swap partition, and setting /etc/fstab (swap) to that uuid).  Note that this must be the same uuid I used for ubuntu 12.04, but is not the one that xubuntu originally had.  But it still won't recover the hibernated apps.
Any further suggestions for getting all OS partitions to hibernate to the same swap partition (not all at the same time)?

---

### Post by sudodus on 2015-01-15
It is allowed to have the same partition for swap, but it is *not* a good idea if you hibernate, because booting into another system (than the one hibernated) will screw things up.

My systems boot quickly and I avoid hibernation :-P

---

### Post by Ralph L on 2015-01-15
I found the problem and corrected it.  The uuid of the swap partition to resume from is in /etc/initramfs-tools/conf.d/resume.  This is explained at: [http://ubuntuforums.org/showthread.php?t=2260722](http://ubuntuforums.org/showthread.php?t=2260722) .  The following code changed the resume uuid to my new swap partition uuid: ```
sudo gedit /etc/initramfs-tools/conf.d/resume
changed this line to new uuid:  resume=UUID=e4ba1f73-8247-4ed2-bf19-eaa4b0f164df
sudo update-initramfs -u
```  I got the new uuid from right-clicking the partition in gparted and selecting "information"
NOTE:  I did not have to update /etc/default/grub as instructed by the web site above.

---

### Post by sudodus on 2015-01-16
Thanks for sharing your solution :-)

---

### Post by malfeasance on 2015-10-14
> **Ralph L said:**
> I found the problem and corrected it.  The uuid of the swap partition to resume from is in /etc/initramfs-tools/conf.d/resume.  This is explained at: [http://ubuntuforums.org/showthread.php?t=2260722](http://ubuntuforums.org/showthread.php?t=2260722) .  The following code changed the resume uuid to my new swap partition uuid: ```
sudo gedit /etc/initramfs-tools/conf.d/resume
changed this line to new uuid:  resume=UUID=e4ba1f73-8247-4ed2-bf19-eaa4b0f164df
sudo update-initramfs -u
```  I got the new uuid from right-clicking the partition in gparted and selecting "information"
NOTE:  I did not have to update /etc/default/grub as instructed by the web site above.

Hey Friend,

You're link is just the link for this thread. I sure would like to see that other thread because I've done everything up to your solution but still no hibernation. I have been searching and searching, maybe I'll come across it. I've seen edits to /etc/default/grub that are explained as possibly for before 12.04 but it's not clear, nor is there an alternative given for later builds. [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) It's just to add the resume line to grub directly. However, I haven't tried that yet...

Thanks!

---

