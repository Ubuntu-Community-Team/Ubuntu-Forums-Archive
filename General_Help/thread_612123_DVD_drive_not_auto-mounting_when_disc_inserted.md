---
title: "DVD drive not auto-mounting when disc inserted"
date: 2007-11-13
forum: General Help
---

### Post by herbster on 2007-11-13
My fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c3a1a86c-b730-4e6c-aeb0-49da8e88d1a1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=f95565d9-b747-43f9-9cc3-d1630cf77eaa /home           ext3    defaults        0       2
# /dev/sdb3
UUID=310b7b87-0c52-4f4e-add7-1c30d9fed9ee /media/bobby    ext3    defaults        0       2
# /dev/sda4
UUID=dbf82137-d915-48cf-a729-95a34a67cdf4 /media/extra    ext3    defaults        0       2
# /dev/sdb1
UUID=9850f8ff-b9f4-4bbd-9e52-a6ea4a461a2b /media/feistyhome ext3    defaults        0       2
# /dev/sdb2
UUID=a3889ed1-1210-4cd5-8fc4-9309ba6039fc /media/feistyroot ext3    defaults        0       2
# /dev/sda2
UUID=f603a8f1-4d2a-4553-b935-55c53840a588 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

It just started happening recently. I put a DVD in and I always have to right-click the drive icon in Nautilus and cilck Mount Volume. In Preferred Applications and Removable Drives and Media I have it set to auto-play DVDs.

:confused:

---

### Post by davidbenson on 2007-11-17
I've got a ThinkPad T61 running Gutsy 7.10 and I'm seeing a very similar problem.  I don't have an answer yet but...

If I insert an external USB drive or a USB-anything-with-a-filesystem, Gutsy mounts it, places an icon on my desktop (Gnome) and opens a window displaying the contents.  If I insert a DVD or CD (blank or otherwise), I get nothing...  Nada...  To work around the problem, I do the following:

1. Click on the Places menu (top, left)
2. Click the Computer entry
3. Double-click the "CD-RW/DVD+/-RW Drive" icon

Note: This shows me my root partition (/) but spins up the drive and mounts it...  Desktop icon appears.

4. Click the Back button (top, left)

Note: Now the CD Drive icon looks like a CD - it looked like a generic drive prior to step 3.

5. Double-click the CD-RW icon again (basically, repeat step 3)

At this point, I can view the contents of the CD/DVD.  DVD movies will play but I have to manually specify the drive (dvd://) in the location box (unique to each app [vlc, mplayer, totem).  Burning CD and DVD media works.

On my Edgy desktop, things work better.  If I insert a CD or DVD, it gets automounted, icon displays on desktop and a window opens to browse contents.  If the media is blank, I get a dialog asking me if I want to burn the disc or ignore it...  I want it to work the same on my laptop...

I did find a reference to AHCI vs. COMPATIBILITY sata setting in the bios, which I tried but without success...  

Any ideas?  -Thanks

---

### Post by herbster on 2007-11-17
david,

Yeah, that process is equal to right-clicking the CD/DVD drive icon and clicking "Mount Volume."

Mine has just stopped automounting recently, out of nowhere. It's baffling me! :confused:

---

### Post by davidbenson on 2007-11-19
I've found a few postings on the Net about Gutsy not being able to automount optical media but nobody has really provided a solid answer yet.  The closest I've seen is a reference on this page:

[http://ubuntuforums.org/showthread.php?t=471563&page=19]("http://ubuntuforums.org/showthread.php?t=471563&page=19")
(search the page for "auto mount")

Unfortunately, I was not able to get mine working by changing AHCI to compatability mode and the thread didn't specify if that setting had to be changed before the install or if it didn't matter.  Either way, I'm not reinstalling to fix it...

Based on the ACHI thing, I was starting to get the impression that SATA support is still a bit sketchy and since my optical drive is SATA, maybe that would explain it...  But looking at your fstab, it looks like yours is IDE/ATA...?  So much for that theory...

At this point, I'm at a complete loss...

---

