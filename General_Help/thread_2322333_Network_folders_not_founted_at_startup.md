---
title: "Network folders not founted at startup"
date: 2016-04-27
forum: General Help
---

### Post by gtozzi on 2016-04-27
Hi there!

I have some network folders booted at startup.
They are **required** before the graphical login is started.

**Sometimes**, there folders are not mounted correctly. I can login to a terminal and type "mount -a" to mount them, or reboot and try again.

Could you please help me solve this?

/etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# New SSD root
UUID=5886aabf-68fb-4223-9329-d84d19af22ee / ext4 defaults,discard 0 0
# New SSD boot
UUID=75ea7fad-16a0-4ab8-82a7-0f6d5a7c92e7 /boot ext3 defaults 0 1
#Swap
/swapfile    none        swap    sw            0    0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

#Aux
UUID=ee734333-f19e-4963-9957-bda93f343ecc /mnt/aux btrfs defaults 0 2

#Network FS
//transylvania/Dati /mnt/dati cifs rw,nouser,auto,file_mode=0600,dir_mode=0700,credentials=/etc/samba/credentials,iocharset=utf8,soft 0 0
//transylvania/Extra /mnt/extra cifs rw,nouser,auto,credentials=/etc/samba/credentials,iocharset=utf8,soft 0 0
//transylvania/Recordings /mnt/recordings cifs rw,nouser,auto,credentials=/etc/samba/credentials,iocharset=utf8,soft 0 0

#USBK
UUID=547e1dfe-d945-4989-8afc-18ae2193356d /mnt/sdk auto ro,user,noauto 0 0

#Tmp
tmpfs        /tmp        tmpfs size=100%,nodev,nosuid,mode=1777    0    0

#NFS bind
/var/www    /mnt/exported    none    bind    0 0
```

The folders that are not mounted are the ones in the "Network FS" group.

---

### Post by nerdtron on 2016-04-27
Hi,

It could be caused by the network interface is not yet UP during startup when the fstab entries are mounted, thus resulting to failure on mounting network drives.

Try to add the following mount options, which will try to wait for the network before the mounting the fstab entry: _netdev,comment=systemd.automount

Example:
```
 //transylvania/Dati /mnt/dati cifs **_netdev,comment=systemd.automount**,rw,nouser,auto,file_mode=0600,dir_mode=0700,credentials=/etc/samba/credentials,iocharset=utf8,soft 0 0
```

Links: 
[http://askubuntu.com/questions/399643/cifs-mount-through-fstab-not-mounting-at-boot](http://askubuntu.com/questions/399643/cifs-mount-through-fstab-not-mounting-at-boot)
[http://askubuntu.com/questions/691998/ubuntu-15-10-cifs-not-mounting-on-bootup](http://askubuntu.com/questions/691998/ubuntu-15-10-cifs-not-mounting-on-bootup)

---

