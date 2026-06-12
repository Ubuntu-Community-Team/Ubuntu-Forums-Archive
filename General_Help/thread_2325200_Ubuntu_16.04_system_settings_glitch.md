---
title: "Ubuntu 16.04 system settings glitch"
date: 2016-05-20
forum: General Help
---

### Post by mdontsov on 2016-05-20
Hello,

Today after powering up my laptop i discovered that some of the Gnome settings have changed. By clicking gear icon in top right corner the System System menu won't appear at all and also i noticed that system tray does not display all the required information i've set up. Then i opened System Settings from the main Application menu and this is how it looks now. Only one question is being raised "Ubuntu, wtf is going on?"

 [ATTACH=CONFIG]269178[/ATTACH]

---

### Post by jim_deadlock on 2016-05-20
Have you changed your theme lately? That could be the cause of the unusual settings panel. Try Tweak Tool or Unity Tweak Tool and change your desktop theme to something else and see if that helps.

It would also help us to help you if you specify which particular settings you're having a problem with.

---

### Post by mdontsov on 2016-05-20
Well that glitch is most likely caused by system disk failure. At least the live usb 'df -h' command returns as follows

Filesystem      Size  Used Avail Use% Mounted on
/cow            7.8G   97M  7.7G   2% /
udev            7.8G  4.0K  7.8G   1% /dev
tmpfs           1.6G  1.4M  1.6G   1% /run
/dev/sdb2       4.9G 1007M  3.9G  21% /cdrom
/dev/loop0      963M  963M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           7.8G  1.1M  7.8G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            7.8G   76K  7.8G   1% /run/shm
none            100M   76K  100M   1% /run/user
/dev/sdb1       145G   90G   55G  63% /media/ubuntu/WD_PASSPORT

The primary drive (256G) is not listed

---

