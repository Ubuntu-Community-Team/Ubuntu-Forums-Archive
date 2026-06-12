---
title: "[SOLVED] Recover non-booting, but otherwise intact Ubuntu?"
date: 2008-02-25
forum: General Help
---

### Post by mithbuntu on 2008-02-25
Hi all,

I've been stuck with this problem for the past month, so I'd really appreciate some feedback or suggestions.

Almost randomly, my ubuntu stopped booting completely. I know I changed the desktop resolution with dpkg configure and downloaded some updates, but that's it.  I'd make it past grub, but the second the boot screen with the progress bar would pop up, the booting would stall completely.  Not one millimeter on the progress bar was made, so I'm assuming there's a problem somewhere in the early boot up of the kernel, but I have no idea where to start.

I'd be open to completely reformatting and install ubuntu again, but I don't want to lose my set up.  If i really had to reformat, would anyone mind helping me find a way to save my amarok mysql database (i can access all my files with the live cd, i just can't run the os to export the mysql database through the live cd).  If I could at least save this, I'd be happy.  The rest I can transfer onto a USB drive, but the mysql database is hidden and I don't know where it is to transfer.

Also, is there anyway to install over my old install?  I figure that might fix my problem without deleting my sql databases.

thanks,

---

### Post by SpaceTeddy on 2008-02-25
edit the grub line and take out the splash and quiet from the kernel (edit by pressing e to enter edit mir, then e again to edit a line).

that will show you the bootlogs and you can see where your computers hangs itself from a tree

---

### Post by mithbuntu on 2008-02-25
Thanks...

it's the same thing I was seeing with recovery mode bootup.

last few lines before error:
```

hda: cache flushes supported
hda: hda1
hdab: max request size ###KiB
hdb: #### sectors (20###MB) w/ ###cache, CHS = ####/63, UDMA(133)
hdb: cache flushes supported
hdb: hdb1 <hdb5>
hdd: ATAPI 126x DVD-ROM ....
Uniform CD-ROM driver revision: ....
scsci 4:0:0:0: Direct Access Canon MP Memory Card 0100 PQ:0 ANSI:0
sd 4:0:0:0: [sdd] Attached SCSI removable disk
sd 4:0:0:0: Attached scsi generic sg3 type0
Done.

```

****here's where it gets interesting

```
Check root=bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
Alert /dev/disk/by-uuid/0353b403-f83d-4e2e-9a74-3f47309-cc133 does not exist.  Dropping to a shell!

Busybox (blah blah version)

```

Now I have this console prompt:

(initramfs)

I can't run mysql or anything but basic commands like ls =/

---

### Post by SpaceTeddy on 2008-02-26
i am not quite sure i know how to fix this. Looks like your hd is not found anymore... either your uuid changed, or your configuration has a bug somehwere.

check your /etc/fstab against the uuid of your hd if they match (can do that with a live cd). you get the uuid with 
> sudo vol_id device

otherwise, i would have to google and try around aswell :(

---

### Post by mithbuntu on 2008-02-26
Thanks teddy!

Using the command above I was able to find the volume's changed uuid (i guess one of the updates did that...) and fix it in grub.

I'm finally back in my linux setup after a couple months:)

---

