---
title: "Help with disk out of space issue"
date: 2020-04-08
forum: General Help
---

### Post by bigwinston2 on 2020-04-08
Hey,

Transmission is claiming it can no longer download with the error message "Error: Unable to save resume file. No space left on device".

Transmission is saving to the network path (which is really on the same device as my Ubuntu Server is running on a VM on my NAS and this x.x.x.78 address is my NAS).

This is the only clue I have. My download path is fine and theres plenty of space provisioned to the VM, what drive/issue/etc could be causing this?

Thanks


```

Filesystem                         1K-blocks       Used  Available Use% Mounted on
udev                                  472932          0     472932   0% /dev
tmpfs                                 100876        968      99908   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv    4062912    4024916          0 100% /
tmpfs                                 504360         12     504348   1% /dev/shm
tmpfs                                   5120          0       5120   0% /run/lock
tmpfs                                 504360          0     504360   0% /sys/fs/cgroup
/dev/loop1                             93568      93568          0 100% /snap/core/8689
/dev/loop0                             96128      96128          0 100% /snap/core/8935
/dev/sda2                             999320     228808     701700  25% /boot
//192.168.0.78/homes/bkg/VmMirror 3746098056 2448412696 1297685360  66% /mnt/nas
tmpfs                                 100872          0     100872   0% /run/user/1000

```

---

### Post by lvm on 2020-04-08
You have no space left on root filesystem, and when that happens, usually almost everything fails because of inability to write logs, temporary files, etc.

---

### Post by wildmanne39 on 2020-04-08
It looks like your root partition is full, when this happens you can no longer install applications or save files, not sure if it is still the case but if my memory serves me correctly the computer may not boot again if it is shut down.
> /dev/mapper/ubuntu--vg-ubuntu--lv    4062912    4024916          0 100% /

[https://askubuntu.com/questions/57994/root-drive-is-running-out-of-disk-space-how-can-i-free-up-space](https://askubuntu.com/questions/57994/root-drive-is-running-out-of-disk-space-how-can-i-free-up-space)

---

### Post by bigwinston2 on 2020-04-08
Alright, thanks for the help.  I didnt realize that drive was root (I just looked in the left column, not the right!) :lolflag:.

---

### Post by Topsiho on 2020-04-08
If your computer still boots you might try and reclaim some (or (very)  much?) space using

sudo apt clean
sudo apt autoremove

with every update many Mb's  are downloaded, and used for the update. If you don't clean them from you drive they remain there, and acumulate until your drive is full.
If your kernel is replaced, you can use autoremove to remove old kernels except the last two ones, and some other not anymore used files, and so free much space on your drive.

Topsiho

---

### Post by oldfred on 2020-04-08
I thought with LVM the partition was always full as it shows the entire partition taken up by the volume.
You need to check use inside your volume(s).

---

