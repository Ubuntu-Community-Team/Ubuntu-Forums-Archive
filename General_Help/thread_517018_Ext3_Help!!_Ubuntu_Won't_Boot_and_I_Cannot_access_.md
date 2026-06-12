---
title: "Ext3 Help!! Ubuntu Won't Boot and I Cannot access files"
date: 2007-08-04
forum: General Help
---

### Post by medicineman24 on 2007-08-04
Ok. I'm kind of a Linux/Ubuntu noob but I'll do my best.  

I have a windows/ubuntu dual boot set up and i keep most of my files (mp3's/jpg's/avi's) on the Ubuntu ext3 partition. I access the files through windows with the help of an application (idk which). Anyway I hadn't booted ubuntu in a while and I had added a couple hundred files to the ext3 from windows.  Ubuntu wouldn't boot but was stuck with the loading cursor going around and around.  I pressed ctrl-alt-backspace and the screen read:

FATAL: error inserting sonypi (/lib/modules/2.6.20-16-generic/kernel/drivers/char/sonypi.ko) : No such device

*starting powernowd...
/etc/rc2.d/s20powernowd:156: cannot create /sys/devices/system/cpu/cpu0/cpufreq/scaling_governer : Directory Non-existent
*CPU frequency not supported

* (blah)
* (blah)
* (blah)
* Running local boot scripts (/etc/rc.local)

Anyway I restarted the computer and booted xp and when i tried to access the partition it stated that "the drive is not formated... do i want to format?" I also ran fsck and it found no errors. I really need help as all my music library and pictures are on this drive. Sorry about the long post.

---

### Post by buzzmandt on 2007-08-04
try running the live cd and see if it can access the drive with your music and pics...maybe you can save them still

---

### Post by medicineman24 on 2007-08-04
Ok. How would i access them from the live cd? Only root can access my files.  I ran "sudo nautilus" but then i can only access the filesystem on the ram from the live cd. I'm kinda a noob so yea.  I need 1000 permission.

---

### Post by strabes on 2007-08-04
You have to mount it manually. Assuming your ubuntu's partition is located at /dev/sda2, ```
sudo mkdir /data
sudo mount /dev/sda2 /data
```

Then plug in your drive and copy them. Why don't you just set up a dedicated data partition that is shared between ubuntu and windows? That's what I have and it works great if I want to listen to some tunes while playing CS or something.

---

