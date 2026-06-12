---
title: "Clicking on HDD recreates the symlinks from previous boot"
date: 2015-06-13
forum: General Help
---

### Post by avro2 on 2015-06-13
Hello,

I'm having this weird issue where whenever I reboot, log in, and open my storage HDD containing my symlinked targets, it fixes the broken symlinks.

I have Ubuntu 14.04 installed and running on my SSD and I've moved some folders (like Music, Pictures, Downloads, etc) to my storage HDD and (soft) symlinking them back into /home/myusername. Trouble is, everytime I reboot the symlinks are broken. Interestingly, whenever I open my storage HDD by double-clicking it fixes the broken symlinks. Does it cause the HDD to suddenly be recognized as a mounting partition? Is there a way to get that command (if there is one) to run at boot? I've read up on modifying the /etc/rc.local file with the symlinks commands but that doesn't seem to work. 


In short: Why does opening my HDD fix my broken symlinks, and can I make Ubuntu use it at boot?

Specs:
Ubuntu 14.04 LTS
Memory: 5.8GiB
Processor: Intel Core i7 CPU 940 @ 2.93GHz x8
Graphics: Gallium 0.4 on AMD TAHITI
OS Type: 64-bit
Disk: 109.6GB

---

### Post by oldfred on 2015-06-13
You should be mounting the HDD with fstab if an internal drive.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Copy template from this thread into your fstab with your UUID & your mount point.
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

     typical fstab entry For ext4, copy & paste into fstab with correct UUID & mount point:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

This will show mount once you have mounted it, usually in /media which is more for external or temporary mounts. But lots of discussion on correct folder/location to mount and no one right answer. I use /mnt/data so it does not show in Nautilus as I have all folders linked and do not want to see them twice, once invalid.  The /media mounts may show twice, not sure with newest versions.

 
mount

---

### Post by coffeecat on 2015-06-13
Not a Forum Feedback & Help thread.

*Thread moved to **General Help**.*

---

### Post by avro2 on 2015-06-13
Hey thanks Oldfred! The first link you provided worked.

Marking this post as [SOLVED].

---

