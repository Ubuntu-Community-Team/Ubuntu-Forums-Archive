---
title: "No option for DVD drives in 'Removable drives and media'?"
date: 2008-04-29
forum: General Help
---

### Post by MangasColoradas on 2008-04-29
I am sure they were there in Gutsy but now in Hardy there are no options at all for CD/DVD drives, just PDA's, cameras, input devices and printers.

Is it somewhere else?

---

### Post by bmac on 2008-04-29
I don't know if this is exactly what your looking for but you can select what software open when DVD's and other media is inserted.

Open "file manager"
edit/preferences
select media from tab

Hope this helps...

---

### Post by MangasColoradas on 2008-04-29
Thanks but thats not it, I am talking about 'System-Preferences-Removable drives and media', it had an option to stop the auto-mounting of DVDs etc.

I noticed DVDs werent mounting so I wanted to check...however since then I have found they wont mount at all unless I do ```
sudo mount /dev/cd0
```

The drives shown in 'Places-Computer' still wont respond though...

---

### Post by mc4man on 2008-04-29
> I am talking about 'System-Preferences-Removable drives and media', it had an option to stop the auto-mounting of DVDs That's now in preferences-> file management  (must 1st. be enabled from edit menus, in preferences section
if you get a chance run ```
sudo lshw -C disk
``` and post

---

### Post by MangasColoradas on 2008-04-30
Yes it seems youre right, sorry bmac!

```
:~$ sudo lshw -C disk
[sudo] password for stone: 
  *-cdrom:0               
       description: DVD writer
       product: DVD_RW ND-3500AG
       vendor: _NEC
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 2.18
       serial: [_NEC    DVD_RW ND-3500AG2.1804110500
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted
  *-cdrom:1
       description: DVD writer
       product: DVD RW AD-5200A
       vendor: Optiarc
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /media/cdrom1
       version: 1.00
       serial: [Optiarc DVD RW AD-5200A 1.00 Oct22,2007
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom1
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
  *-disk:0
       description: ATA Disk
       product: WDC WD1200JS-00M
       vendor: Western Digital
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 02.0
       serial: WD-WCANP1011657
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=7c3f7c3f
  *-disk:1
       description: ATA Disk
       product: ST3120026AS
       vendor: Seagate
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 3.56
       serial: 3JS44RTV
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=8cb3ca15

```

---

