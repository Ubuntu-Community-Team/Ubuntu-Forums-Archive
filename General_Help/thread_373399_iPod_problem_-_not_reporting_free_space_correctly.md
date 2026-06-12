---
title: "iPod problem - not reporting free space correctly"
date: 2007-03-01
forum: General Help
---

### Post by cisforcojo on 2007-03-01
Hey all,

I have an iPod Mini and when I plug it into the USB, it only registers as having 6 MB free....
but in Windows it registers as having 2.22GB free. I like the Windows report more (though I hate to admit it). What could be causing this? It prevents me from being able to transfer files to the ipod in Linux. Windows, no problem.

My /etc/fstab entry looks like this:
/dev/sda2 /media/ipod vfat   defaults,user,noauto,sync,umask=000

My FIRST sync with the ipod transferred files. Ever since then, it's reported only having 6MB free in ubuntu. This is a very confusing problem. Any help is appreciated!

---

### Post by cisforcojo on 2007-03-02
Does ubuntu reserve space on removable media? When I first connected the iPod, I had a LOT of free space on it. Then I removed some songs, sync'd, and there was no indication that any space had been freed. Then I deleted the .Trash folder and still no luck.  (I did none of this as root).
Windows reports the free space correctly, NOW I deleted everything on the ipod and it reports having 1.3GB free. (There's 4GB). The only thing I can think of is that Ubuntu is somehow reserving space for those files that I deleted but never actually got rid of (they were gone but now there's still no free space.) Any ideas??????

---

### Post by cisforcojo on 2007-03-02
It's reported as having 4096MB so that's correct.
dmesg output:

[17261440.292000] usb-storage: device scan complete
[17261440.296000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17261440.296000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17261440.296000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[17261440.296000] sda: Write Protect is off
[17261440.296000] sda: Mode Sense: 64 00 00 08
[17261440.296000] sda: assuming drive cache: write through
[17261440.300000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[17261440.300000] sda: Write Protect is off
[17261440.300000] sda: Mode Sense: 64 00 00 08
[17261440.300000] sda: assuming drive cache: write through
[17261440.300000]  sda: sda1 sda2
[17261441.952000] sd 4:0:0:0: Attached scsi removable disk sda
[17261441.952000] sd 4:0:0:0: Attached scsi generic sg0 type 0
[17261443.448000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!


When I right click the ipod icon on my desktop and goto properties to check free space, it says 1.3GB. But there are no files on the ipod. Any idea why it would have this disparity?

---

### Post by Redwood on 2007-03-12
I am having the exact same problem as you have described here.  Initially there was the .trash hidden away on there, but even after removing that completely it is only reported as 1.3 gb free.  Very frustrating.

Did you ever solve this problem?

---

