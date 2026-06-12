---
title: "External hard drive (backup) only connected during backups. AutoMount?"
date: 2023-03-30
forum: General Help
---

### Post by 777funk on 2023-03-30
I assume in this case, I should do nothing other than format and name the drive (no automounting). Is this correct? In other words, it should show up in:
/media/home/user/

 If I recall, automounting is only for installed drives and doesn't work for a drive plugged live into eSATA or USB2.0/3.0/etc.

---

### Post by TheFu on 2023-03-30
**autofs** provides the ability for "sometimes connected" storage to be mounted and umounted as needed, automatically. I use it for all USB connected storage. I do not use it for eSATA/InfiniBand connected storage, but it would work there too.

With **autofs**, you can control where storage is mounted and the mount options used, which would depend on the file system(s) involved.

There is a How-To guide that is easily found by doing a web-search for "autofs ubuntu". It doesn't touch the /etc/fstab.

For most temporary storage connections - let's not use the term "drive", since that is almost never what we mount. We mount file systems which are usually in partitions, BTW.  Anyway - if we add a unique LABEL to the file system/partition, then we can mount that file system using the LABEL=  rather than using UUID= or hunting down the current device file, which can change from boot to boot.  It is possible to us any of the generated symbolic links under /dev/disk/ to mount storage too.
```
$ ls /dev/disk/
by-id/  by-label/  by-partlabel/  by-partuuid/  by-path/  by-uuid/
```
In those subdirectories, are symbolic links that are correct by the specific object type which point to the current, correct, device file on our systems.  Anyways, these are also options for mounting.

So, you can setup autofs to know about a specific "backup" partition (file system) on an external storage device. After the device is connected, give autofs about 5 seconds, then just access that storage to cause it to be mounted.  As long as there are open files on the device, it will remain mounted.  Do whatever you do for backups, hopefully, using a real backup tool and not just copying files over, then ensure all the files on the backup storage are closed and wait 60 seconds.  Then autofs will umount the storage automatically and you can unplug the USB connection.  Does that sound like something you'd want?

autofs can make SDHC, microSD, USB flash storage and almost any other temporary storage easy to use without the security risks and bad default options that gvfs uses.  autofs uses real mounts which are much faster (almost always) than gvfs too.

---

### Post by 777funk on 2023-03-30
> **TheFu said:**
> **...**

All very good info and thank you! And yes, I use a backup tool. I like GUIs, so I use RSync with the GUI called Luckybackup.

---

### Post by mikodo on 2023-03-31
> **TheFu said:**
> Then autofs will un-mount the storage automatically and you can unplug the USB connection.  Does that sound like something you'd want? I apologize to the OP for jumping in here.

Yes. This is what I want to do.  

Question: 

Will the external nodes/drives be **off** by being unmounted. I ask, because I want to run the backups, (by using  Cron/anacron. When I turn on my computer, I want to have Cron/anacron to send the command to mount the external nodes, and run the backups. Then unmount them. When the backups are run and the nodes are unmounted by anacron,  I may not remember to yank their usb connections.  

Edit: Or, I might just have Anacron run the mount commands for the nodes, then run the commands for rdiff-backup, then have it run the umount commands. That I know about. Anyways ...

Thank you.

---

