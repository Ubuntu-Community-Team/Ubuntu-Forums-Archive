---
title: "[SOLVED] Updates to 8.04 keep getting dpkg --configure -a error"
date: 2008-05-13
forum: General Help
---

### Post by uclalinux on 2008-05-13
```
uclalinux@uclalinux-desktop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1
```

What should I do?

---

### Post by plucky on 2008-05-13
From a terminal ```
df -h
``` and see if your boot or root partition is full.

---

### Post by uclalinux on 2008-05-14
```
uclalinux@uclalinux-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              92G   72G   15G  83% /
varrun               1008M  224K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  136K 1008M   1% /dev
devshm               1008M  384K 1008M   1% /dev/shm
lrm                  1008M   38M  970M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3              45M   37M  5.3M  88% /boot
/dev/sda1              59G   22G   38G  37% /home/uclalinux/windows_partion
/dev/sdb1             294G  229G   50G  83% /home/uclalinux/sdb1
/dev/sdc1             230G  160G   58G  74% /home/uclalinux/sdc1
/dev/scd0             635M  635M     0 100% /uclalinux/cdrom0

```

---

### Post by plucky on 2008-05-14
> /dev/sda3              45M   37M  5.3M  88% /boot


I think this is your problem.You need to increase the size of this partition using the **Live CD**.

Good Luck

---

### Post by uclalinux on 2008-05-14
Thank you for your idea, 
but I did the live update, so the 15GB in the boot, so I don't think is an issues, have about .750 Tb on my comp.  I think it is a converting error.t

---

### Post by plucky on 2008-05-14
uclalinux@uclalinux-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              92G   72G   15G  83% /
varrun               1008M  224K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  136K 1008M   1% /dev
devshm               1008M  384K 1008M   1% /dev/shm
lrm                  1008M   38M  970M   4% /lib/modules/2.6.22-14-generic/volatile
[color=red]/dev/sda3              45M   37M  5.3M  88% /boot[/color]
/dev/sda1              59G   22G   38G  37% /home/uclalinux/windows_partion
/dev/sdb1             294G  229G   50G  83% /home/uclalinux/sdb1
/dev/sdc1             230G  160G   58G  74% /home/uclalinux/sdc1
/dev/scd0             635M  635M     0 100% /uclalinux/cdrom0


According to this output,you have a separate boot partition on /dev/sda3 which is 88% full.The **sudo dpkg --configure -a** is trying to generate a **/boot/initrd.img-2.6.24-16-generic** image which goes into the /boot partition,but cannot do so because it is nearly full.

If I am wrong,I am sorry,but I can only go by what I can see.


Good Luck

---

### Post by chrisccoulson on 2008-05-14
The lack of space on /boot is definately the issue, as dpkg fails when trying to run update-initramfs, which needs space on /boot for the new initramfs

---

### Post by uclalinux on 2008-05-14
How should I increases the space, can I remove the old files on the boot, and if so what files should I remove?

---

### Post by plucky on 2008-05-15
> **uclalinux said:**
> How should I increases the space, can I remove the old files on the boot, and if so what files should I remove?

To increase the space you will need to either boot the LIve CD and use the Partition editor or download the [Gparted live CD](http://gparted.sourceforge.net/livecd.php) and use that.

I would increase the space to 100M to give yourself breathing room.

When you change a partition,the UUID will change and so you have to make changes to your /etc/fstab file to reflect the new UUID.


If you want to just make more space,you could possibly get rid of the previous kernel using **synaptic package manager**.To see what your boot partition contains use ```
cd /boot
ls -lh
``` in a terminal window.


Good Luck

---

