---
title: "boot-repair"
date: 2015-08-10
forum: General Help
---

### Post by Jerry_Oram on 2015-08-10
I accidentally wrote to my boot device "/boot" while attempting to write a ScanDisk.
/Boot now shows up with 0 space left (df -k):
Filesystem                             1K-blocks                 Used Available Use% Mounted on
/dev/mapper/ubuntu--vg-root            472132904             97157836 350969028  22% /
none                                           4                    0         4   0% /sys/fs/cgroup
udev                                     8157652                   12   8157640   1% /dev
tmpfs                                    1633768                 1628   1632140   1% /run
none                                        5120                    0      5120   0% /run/lock
none                                     8168828                 1584   8167244   1% /run/shm
none                                      102400                   40    102360   1% /run/user
/dev/sda1                   18446744073709543756 18446744073709461909     81847 100% /boot
/dev/sdb1                                7819316               219952   7599364   3% /mnt/boot-sav/sdb1

I have been trying to recover/restore /boot with no luck so far. When I run the "boot-repair" tool it seem to run forever and do nothing.
Any ideas on how I can fix this colossal mistake? I have not rebooted so I am still up and working fine. This is my version of ubunto:

oram@joram:/$ uname -a
Linux joram 3.13.0-55-generic #94-Ubuntu SMP Thu Jun 18 00:27:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by VMC on 2015-08-10
boot-repair can't help you with missing kernels. Look at this thread for help:
[http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)

---

### Post by oldfred on 2015-08-10
If you have not rebooted (and do not) then you do not need to chroot as you are already in your system.

You probably cannot copy a backup into /boot as you are running one kernel in /boot, so it cannot be copied. You can flag for delete but then when you reboot it is deleted.

 Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

   RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

      
 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
sudo apt-get -s autoremove
# one line purge
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
I prefer synatic and keeping 2 kernels, current and one known working older on.

 In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls -l /boot/vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.13.0-{XX,XX,XX,XX,XX,XX}-generic
sudo apt-get purge linux-image-3.13.0-{54,55,57}-generic
Also headers:
dpkg -S /usr/src/*
Example, some did not have -generic at end:
sudo apt-get purge linux-headers-3.13.0-39-generic
sudo apt-get purge linux-headers-3.13.0-{40,43,46,48,49,51,53,54,55,57}-generic
 Cleans up both /lib/modules & /usr/src

---

