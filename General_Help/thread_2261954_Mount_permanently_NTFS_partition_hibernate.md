---
title: "Mount permanently NTFS partition hibernate?"
date: 2015-01-22
forum: General Help
---

### Post by Hesediel on 2015-01-22
In my pc always to mount the partition in where there's windows installed i have to run this command in terminal

```
sudo mount -t ntfs-3g -o remove_hiberfile /dev/sda2 /media/Windows
```

I have disabled  fast boot in windows, disabled password....the system (xubuntu) does not mount the partition always, if i reset, if i shut down ecc..

I would like to mount directly tis partition....is stressing always the startup blocked announcing unable to mount the partition press S....and always run terminal to give the command

---

### Post by ajgreeny on 2015-01-22
I think you need to disable **fast-startup**, not **fastboot** in windows, which I beleive are two different things, but I'll have to let you find details as I no longer run windows of any kind, and I don't know if that setting is in the BIOS/UEFI or is a windows setting within the OS.

You will also need to edit the /etc/fstab file as root and add a line for the partition at the bottom to mount the Windows partition at boot time.

For this you need the UUID of partitions, as that is more reliable than using the /dev/sda2 that you have used.
Get UUIDs with command ```
sudo blkid -c /dev/null
```then, assuming you already have the /media/Windows folder made on your system add
```
UUID=66E53AEC54455DB2 /media/Windows  ntfs    defaults    0    0
```changing the UUID I show for your own partition.

Save the new fstab and then run ```
sudo mount -a
``` to test it; if there are no errors all is well.

---

### Post by Mark Phelps on 2015-01-22
> I think you need to disable fast-startup, not fastboot in windows, which I beleive are two different things,

You are correct -- they are two different things. However, FastStartup only affects Windows 8 machines and newer.  IF the OP is running Windows 7 or older, it's a different problem.

---

### Post by Ko_Char on 2015-01-22
may be you'll need to turn off hibernate in Windows. [http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html](http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html)
You can check the hibernate file in Windows - "C:\hiberfil.sys". Need to enable hidden system files though.
If you can mount the drive after turning off the hibernate, it might be the issue.

---

