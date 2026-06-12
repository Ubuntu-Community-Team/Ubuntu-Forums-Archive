---
title: "Swap, firefox, amarok and hibernate"
date: 2008-02-23
forum: General Help
---

### Post by funny money on 2008-02-23
I was having problems hibernating whenever I had a lot of open programs with a "No enough swap space" error. I then re-partitioned my hard disk to increase the swap from 500MB to 1GB. After fixing  the fstab, swap gets mounted and using swapon I can see it is being used, however, Amarok kindof hangs between change of songs renaming, etc (it darkens), though not for long(5-50seconds), which it never did before.
Majorly, the reason I increased the swap in the first place is now broken. It says "device not found, try swapon -a" whenever I attempt to hibernate. But the swap is being used:confused:. Any ideas ?!?

---

### Post by mali2297 on 2008-02-24
Check where you have your swap partition,
```

sudo fdisk -l

```
Say it is /dev/sda7. Open the file /etc/initramfs-tools/conf.d/resume in an editor. It should contain the line
```

RESUME=/dev/sda7

```
If not, correct it and save your changes. Then run
```

sudo update-initramfs -u
sudo reboot

```
and try hibernate again.

---

