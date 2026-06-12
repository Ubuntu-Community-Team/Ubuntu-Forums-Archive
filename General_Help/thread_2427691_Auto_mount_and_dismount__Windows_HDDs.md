---
title: "Auto mount and dismount  Windows HDDs"
date: 2019-09-24
forum: General Help
---

### Post by tip32a on 2019-09-24
I would like to use Ubuntu to browse through a bunch of windows HDDs prior to re-purposing them.  

If I take a HDD from a Windows 10 laptop and connect it to a Windows 7 PC, Go to USERS and try to open any of the user profiles Windows asks permission then takes the next 45-60 minutes to allow the viewing of the folder.

I have been told That if I use windows XP or linux I dont have to do that.

Once I mount the drive I have access to the whole files ystem.  (Is this true?  May be a good question.)

What I want to do is plug the test drive into a USB dock.  Have linux prompt me to mount the drive and after agreeing the file manager opens.

Then When I am done I can press some button to dismount the drive.
Thanks Tom

---

### Post by oldrocker99 on 2019-09-25
To dismount the drive, right-click the drive's icon and select "Safely Remove Drive" or "Unmount Drive."

---

### Post by CatKiller on 2019-09-25
The big issue is whether the Windows that was on those drives was shut down properly prior to those drives being removed. Windows 10 *doesn't* shut down properly by default, simply hibernating instead, which leaves NTFS partitions in a dirty state. Ubuntu won't touch *those* partitions with a ten-foot pole.

---

### Post by yancek on 2019-09-25
In addition to the above, how are you planning to use Ubuntu/Linux?  Do an actual install, use a 'live' DVD/USB?  To read/write an ntfs partition from Ubuntu/Linux, you need ntfs-3g installed and I'm not sure that would be available on a 'live' system.

---

### Post by Impavidus on 2019-09-25
If Windows wasn't properly shut down, you may still be able to mount the ntfs partitions in read-only mode, but you have to do that manually.

I think ntfs-3g is available on live disks, but I haven't checked recently. Your Windows file system may even get mounted without asking.

Once you've mounted the filesystem, you have complete access. Linux ignores Windows' permissions system, just as Windows ignores Linux' permissions system.

---

### Post by Yellow Pasque on 2019-09-25
> **yancek said:**
> To read/write an ntfs partition from Ubuntu/Linux, you need ntfs-3g installed and I'm not sure that would be available on a 'live' system.

List of packages included in Live image: [http://releases.ubuntu.com/18.04/ubuntu-18.04.3-desktop-amd64.manifest](http://releases.ubuntu.com/18.04/ubuntu-18.04.3-desktop-amd64.manifest)
ntfs-3g is included (and has been for a while now IIRC).

> Windows 10 doesn't shut down properly by default, simply hibernating instead, which leaves NTFS partitions in a dirty state. Ubuntu won't touch those partitions with a ten-foot pole. 

There are ways around that. You can mount read-only. Or if you want to read/write, you can use the remove_hiberfile option if you don't care about running Windows on the drive ever again.

---

### Post by TheFu on 2019-09-25
Windows also has multiple storage types.  If the partitions are "Basic", accessing it is usually easy.  
Advanced partitioning, encryption, partitions spanning multiple physical drives, will be harder and might be impossible to access.

Give it a try, but keep a Windows10 machine around as a backup technique.

---

