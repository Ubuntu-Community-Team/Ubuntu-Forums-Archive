---
title: "Help on Automounting a USB Drive"
date: 2022-09-06
forum: General Help
---

### Post by machmandp on 2022-09-06
Hi

I tried to set my USB Drive to auto mount and this is what i have is the etc/fstab at the moment

**/dev/disk/by-id/usbdrive /media/plex/usbdrive auto nosuid,nodev,nodev,nofail,noauto,x-gvfs-show 0 0**

but this does not allow the drive to be shared with write permissions on the network

if i manually enter the below into a terminal it works perfectly

**sudo mount -o rw,users,umask=000 /dev/sda1 /media/plex/usbdrive**

Could someone please help me to amend the command above so it works in the fstab file

Thanks

---

### Post by sudodus on 2022-09-06
Create a mount point (or check that it exists)
```

sudo mkdir -p /media/plex/usbdrive

```

Make a **backup copy** of [FONT=Courier New]** /etc/fstab**[/FONT] before you start editing.

[hr][/hr]
Fields in[FONT=Courier New]** /etc/fstab**[/FONT]: See [FONT=Courier New]**man fstab**[/FONT].

Field 1:

If you intend to automount a partition on one particular drive, I suggest that you use the UUID of the partition, that you want to mount. You can use [FONT=Courier New]**lsblk -f**[/FONT] to find the UUID of the partition on ***your*** USB drive.

Otherwise, and if you are rather sure that the drive is almost always seen as **[FONT=Courier New]/dev/sda[/FONT]**, and partition #1, you can use [FONT=Courier New]**/dev/sda1**[/FONT].

Field 2:

The mountpoint: **[FONT=Courier New]/media/plex/usbdrive[/FONT]**

Field 3:

If I understand correctly, the options **[FONT=Courier New]rw[/FONT]** and **[FONT=Courier New]users[/FONT]** are common for all file systems, but **[FONT=Courier New]umask[/FONT]** is only used for Microsoft file systems (FAT32, exFAT and NTFS), so the line we make will probably fail for non-Microsoft file systems, even though we use **[FONT=Courier New]auto[/FONT]** here.

Field 4:

In principle you can use the same options here as in the command [FONT=Courier New]**mount**[/FONT]. I suggest that you use 'defaults' too, but that is optional, [FONT=Courier New]**defaults,rw,users,umask=000**[/FONT]

Field 5 and 6 can be 0 and 0 (zero).

So here is a line that I tested with a FAT32 partition. It should work with exFAT and NTFS too:
```

/dev/sda1  /media/plex/usbdrive  auto  defaults,rw,users,umask=000  0  0

```

The alternative for a FAT32 partition could be (replace my UUID with that of ***your*** partition),
```

UUID=[COLOR="#FF0000"]6CD5-DE0F[/COLOR]  /media/plex/usbdrive  auto  defaults,rw,users,umask=000  0  0

```

If you don't expect the drive to be connected at boot, you should add the option **[FONT=Courier New]noauto[/FONT]** like you have in your post #1. 
```

/dev/sda1  /media/plex/usbdrive  auto  defaults,rw,users,umask=000,noauto  0  0

```
This means that you have to mount the drive manually also when it is connected at boot, but it is enough to specify only the device or only the mount point to mount it.
```

sudo mount /dev/sda1
#or
sudo mount /media/plex/usbdrive

```

---

### Post by machmandp on 2022-09-06
Thanks for the reply i will give that a go

---

### Post by machmandp on 2022-09-06
Thanks for that it worked perfect

---

### Post by sudodus on 2022-09-07
You are welcome :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by HermanAB on 2022-09-07
Note that if you set a unique Volume Name on your USB drive, then it will always mount with the same removable mount point and then you need not futz with fstab.

---

