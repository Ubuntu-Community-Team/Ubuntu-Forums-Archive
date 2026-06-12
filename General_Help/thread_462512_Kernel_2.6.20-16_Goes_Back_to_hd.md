---
title: "Kernel 2.6.20-16 Goes Back to hd*?"
date: 2007-06-02
forum: General Help
---

### Post by moore.bryan on 2007-06-02
*so, when i did my daily aptitude upgrade today, the 2.6.20-16 kernel was installed and now i had to rewrite my fstab because it doens't use the sd* nomenclature; anyone have any ideas why?*

---

### Post by mijj on 2007-06-02
entertainment.

---

### Post by moore.bryan on 2007-06-02
[I]for whom?  not i...
;-)
[/I]

---

### Post by confused57 on 2007-06-02
I believe this occurs with certain hard drive controller chipsets:
[http://ubuntuforums.org/showthread.php?t=456662&page=36](http://ubuntuforums.org/showthread.php?t=456662&page=36)

Drive identification did not change to from sda to hda on my pc, with a Sis 661 chipset.

---

### Post by Azakus on 2007-06-02
Find the UUID numbers for your drives and use those in fstab. That way, there will never be a break as the UUID numbers never, ever change. I think they are essentially a SHA-1 hash of your partitions.
Anyway, look up the UUID numbers with
```

ls -l /dev/disk/by-uuid/
```
This will show the uuid numbers for your drives.
Then edit your /etc/fstab file and put the uuid numbers in place of the harddrive paths
Example
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc1       /mnt/share      vfat    iocharset=utf8,umask=000  0       0

```
Becomes
```

# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=9f0c8d29-65af-43cc-8b47-28a958b7c0e1 / ext3 defaults,errors=remount-ro 0 1
UUID=c49a97e0-e6c6-4b4b-b485-746a34d966be       none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
UUID=452B-13F6 /mnt/share vfat iocharset=utf8,umask=000 0 0

```
And edit your /boot/grub/menu.lst file to replace your root path with UUID=the UUID number of your root partition.
Then update grub with ```
sudo /usr/sbin/update-grub
```

---

### Post by merlinus on 2007-06-02
> 
Find the UUID numbers for your drives and use those in fstab. That way, there will never be a break as the UUID numbers never, ever change. I think they are essentially a SHA-1 hash of your partitions.


I have had mine change when I re-sized a partition.  My guess is that it will also occur when a partition is moved.

-merlin

---

### Post by Azakus on 2007-06-02
> **merlinus said:**
> I have had mine change when I re-sized a partition.  My guess is that it will also occur when a partition is moved.

-merlin

Yeah, that makes sense. I meant that more in the manner that it won't change because of the kernel upgrades. It will most definitely change if you move it, or change it's size, because the SHA-1 hash of the drive will change.

---

### Post by moore.bryan on 2007-06-03
[I]luckily, i already has uuid numbers for my hd, it was an external usb drive which went from sdd1 to sda1 because the hd's were looked at as hda and hdb instead of sda and sdb...
thanks for the input... seems weird that any of this would happen at all, though...
[/I]

---

### Post by Azakus on 2007-06-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is now fixed in the latest kernel.
[http://permalink.gmane.org/gmane.linux.ubuntu.security.announce/558](http://permalink.gmane.org/gmane.linux.ubuntu.security.announce/558)

---

### Post by moore.bryan on 2007-06-09
*the new kernel just upgraded, so i'll check on this when i reboot.  thanks!*

---

