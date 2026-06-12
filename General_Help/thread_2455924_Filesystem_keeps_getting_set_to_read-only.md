---
title: "Filesystem keeps getting set to read-only"
date: 2020-12-30
forum: General Help
---

### Post by EMR on 2020-12-30
I have a shared partitiod, /media/eamonn/shared (partition: /dev/sda6). I've been using it for a while as most of the SSD on this laptop which I'm dual booting with win10. It's now being mounted as read only. When I force-mount it with:

```
sudo mount -o remount,rw /dev/sda6 /media/eamonn/shared
```

It will mount as read/write but as soon as I actually try to write anything, it's set to read-only again. I tried:

```
sudo fsck -n -f
```

Which didn't fix it. I'm not sure what to grep for in ```
dmesg
```. (sda didn't turn up anything obvious)

---

### Post by oldfred on 2020-12-30
Is this an NTFS partition?
Windows updates will turn fast start up back on, setting hibernation flag & preventing Linux NTFS driver from using it in read/write mode.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Post these if not NTFS:
sudo parted -l
cat /etc/fstab
mount

---

### Post by EMR on 2021-01-01
Thanks, that worked!

---

### Post by oldfred on 2021-01-01
Glad that worked.
Please change to solved so others can find thread and know something that may work.

---

