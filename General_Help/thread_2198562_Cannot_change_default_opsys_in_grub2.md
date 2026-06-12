---
title: "Cannot change default opsys in grub2"
date: 2014-01-09
forum: General Help
---

### Post by James Wilde on 2014-01-09
I installed a clean version of Ubuntu 13.10 recently, then, when I discovered a problem with iBus which was not found in 13.04, I installed a clean version of 13.04 side by side with the 13.10.  I have my hard disk partitioned with 20 GB for 13.10, ca 460 GB for /home and 20 GB for 13.04.

I have now solved my problem with 13.10, and want that opsys to be the default.  Twice now I have changed GRUB_DEFAULT=0 to GRUB_DEFAULT=4 and run update-grub.  Still Ubuntu 13.04 is the default.  I noted this rather strange result after running update-grub this second time:

```
james@james-ubuntu:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.8.0-34-generic
Found initrd image: /boot/initrd.img-3.8.0-34-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 13.04 (13.04) on /dev/sda4
done
```

In other words, update-grub finds Ubuntu 13.04 on /dev/sda4, but does not appear to find Ubuntu 13.10 on /dev/sda1.

Can anyone help please?

---

### Post by deadflowr on 2014-01-09
Those top entries are the entries for the device using 13.10.(3.11 kernel)
If you run
```
df -h
```
(really, simply df if you want, the -h is to make the byte sizes human-readable.
You will see that the mount /, should be on /dev/sda1.

Added: If the default, or device listing when booting hasn't changed, it's because the grub version for 13.04 was installed.
boot into the 13.10 version and in a terminal run
```
sudo grub-install /dev/sda
```
It should list NO Errors reported, or something like that.
then update-grub again.

---

### Post by oldfred on 2014-01-09
It might be easier just to boot into 13.10 and reinstall its boot loader into the MBR.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by James Wilde on 2014-01-12
Thanks, guys.  That fixed it.

---

