---
title: "Flash Drive Problem"
date: 2017-09-04
forum: General Help
---

### Post by shane_faulkinbury2 on 2017-09-04
I'm trying to format a flash drive that I used to install Ubuntu and I get the following error.

So I looked for a way to mount the drive on the command line.  I did it and get this error.

```
 ~$ sudo -i[sudo] password for bubba: 
root@bubba-110-194:~# mount -a /
mount: mount point /mnt/usb-SMI_USB_MEMORY_BAR-0:0 does not exist
mount: wrong fs type, bad option, bad superblock on /dev/disk/by-id/usb-Kingston_DataTraveler_2.0_C86000BDB740C080BA27BD9A-0:0,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)


       In some cases useful info is found in syslog - try
       dmesg | tail or so.
root@bubba-110-194:~# dmesg | tail
[19285.077654] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[19285.085782]  sdb: sdb1
[19285.090141] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[19285.354892] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[19495.347141] FS-Cache: Loaded
[19495.368422] RPC: Registered named UNIX socket transport module.
[19495.368425] RPC: Registered udp transport module.
[19495.368425] RPC: Registered tcp transport module.
[19495.368426] RPC: Registered tcp NFSv4.1 backchannel transport module.
[19495.420183] FS-Cache: Netfs 'nfs' registered for caching
root@bubba-110-194:~# fsck
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/mapper/ubuntu--vg-root is mounted.
e2fsck: Cannot continue, aborting.


 
```

Dores anyone know what to do about this now?  I'd really like to format this drive so I don't have to throw it away.

---

### Post by sudodus on 2017-09-04
I suggest that you try with **mkusb**.

If it does not work, the drive might be damaged beyond repair with the tools available to your and me.

See the following links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[Can't format my usb drive. I have already tried with mkdosfs and gparted - Analysis of the problem](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

---

### Post by oldos2er on 2017-09-04
Normally you'd use gparted or its CLI equivalents (parted, fdisk or *.mkfs) to format a partition or flash drive. Not sure why you're using *mount* or *fsck* since neither of them have anything to do with formatting.

---

### Post by shane_faulkinbury2 on 2017-09-04
[COLOR=#000000]sudodus, from your link I can't find how to install [/COLOR][COLOR=#000000]dus or mkusb.  On the link you supplied I've clicked on both and neither make sense on how to install.

[/COLOR][COLOR=#000000]oldos2er, I've tried Gparted, but Disks and the Terminal are easier for me to use at this point.  I've only been using Ubuntu for a year.[/COLOR]

---

### Post by sudodus on 2017-09-05
You can find the details to install mkusb at the following link (or when you scroll down in the first link of my previous post),

[Quick start manual and mkusb PPA](https://help.ubuntu.com/community/mkusb#Quick_start_manual_and_mkusb_PPA)

You can copy and paste the crucial command lines (code) from here to a terminal window:

If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi
```

[hr][/hr]

The [quick start manual](https://help.ubuntu.com/community/mkusb?action=AttachFile&do=view&target=mkUSB-quick-start-manual-12.pdf) might help you get started, because it shows what to expect when installing and using mkusb. Page #27 (of the quick start manual) describes how to restore (a USB pendrive or another drive) to a standard storage device.

---

### Post by shane_faulkinbury2 on 2017-09-05
Thanks again sudodus!  :D

---

### Post by sudodus on 2017-09-05
You are welcome :-)

```
[COLOR="#A52A2A"]if[/COLOR] this helped you solve your problem
[COLOR="#A52A2A"]then[/COLOR]
 please click on **Thread Tools** at the top of the page and mark this thread as SOLVED,
[COLOR="#A52A2A"]else[/COLOR]
 please tell us what your problems looks like now, what you might need, and we will continue to help.
[COLOR="#A52A2A"]fi[/COLOR]
```

---

