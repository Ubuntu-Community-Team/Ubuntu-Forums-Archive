---
title: "Boot Repair Log"
date: 2016-12-12
forum: General Help
---

### Post by lukeca2 on 2016-12-12
Had some trouble lately on my dual boot because of maybe an update, driver problems, or SSD problems not really sure. It affected my windows boot and I couldn't properly use Ubuntu for more than 5 minutes without it bugging out. Basically now both are not properly bootable so using a liveUSB I went through a boot repair and have this log [http://paste2.org/FNnFm9U3](http://paste2.org/FNnFm9U3) help appreciated

---

### Post by oldfred on 2016-12-12
You are now not showing an sda at all?
But Ubuntu was installed when your now sdc was sda?

I have found drive order to be important. Did you plug in a new drive or move drives around. Grub only installs to the ESP - efi system partition on drive seen as sda. But now ESP is sdc2.

You need to have sdc in SATA port 0, and then without skipping ports add drives. You flash drive became sdb which is probably because you skipped a port or two. I used to have that issue where my flash drive would be sdf until I rebooted and it became sdb. Changed to have all drives in port order and issues went away.

You also show Windows fast start up or always on hibernation. That must be off if dual booting.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

But even script is confused on drive order. At top of script it shows no sda, but sdc. But blkid and parted show sda and no sdc. Not seen that before.

---

