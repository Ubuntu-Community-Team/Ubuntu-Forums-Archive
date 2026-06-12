---
title: "Serious Data Loss After Nautilus Crash"
date: 2014-09-15
forum: General Help
---

### Post by witchbutter on 2014-09-15
I was dragging and dropping files between two nautilus windows in Ubuntu 14.04 and suddenly it hung, and then crashed.  After the crash literally everything I have saved ro moved since the last reboot is gone.  I am at a total loss, I have never experienced anything like this in 15 years of using linux.  Is there a way to recover and how can I be sure nautilus won't do this again?

---

### Post by Jonor on 2014-09-16
Although not tried myself, the application testdisk should help.
I don't think you can be sure it won't crash, contingencies are needed.

---

### Post by tgalati4 on 2014-09-17
Check the SMART status of the disk drive.  It's possible your drive overheated and crashed, and that would result in file loss.  I've seen data loss when one drags files to a USB thumb drive and Nautilus shows that it is finished (but it is not!) and pull the drive and files on both sides are missing.  Nautilus thinks it is finished, but everything is pushed to RAM and if you pull the USB stick too soon, those files vanish.  If you properly "eject" the drive, you will get a notification that the drive is in use.  But that doesn't prevent you from pulling the stick out if you are in a hurry.

Open a terminal:

```
smartctl -a /dev/sda
```

Yes *testdisk* or *photorec* (which is part of testdisk) is the tool to use to recover lost files.  Read up on how to use them first.  Get an external drive to capture the files.  Be prepared to recover all of your important files, because you may need a new disk and a new OS installation.

Look in your log files.  If you see disk read or write errors then Nautilus is not the problem.

```
more /var/log/syslog
```

---

### Post by cariboo on 2014-09-17
Before making any changes to the data, I'd suggest running fsck on the partition first.

```
sudo fsck /dev/sda
```

---

