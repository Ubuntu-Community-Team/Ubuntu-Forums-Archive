---
title: "Can grub.bak be removed"
date: 2023-07-01
forum: General Help
---

### Post by caterhamfan on 2023-07-01
Hey all,

I am trying to update, however, I cannot update due to a full /boot. I removed previous kernels but still don't have enough space. 
My first thought would be to extend the partition but don't have time to do this right now.

Can the grub.bak folder be removed safely? It's just the grub backup so should be ok. If it's safe to remove how can I do it? I can't do it in nautilus.

Thank you,

---------------------------------------------------------

total 138M
drwxr-xr-x  6 root root 4.0K Jul  1 23:17 .
drwxr-xr-x 20 root root 4.0K Jun 20 17:06 ..
-rw-r--r--  1 root root 264K Jun 21 15:38 config-5.19.0-46-generic
drwx------  5 root root 4.0K Jan  1  1970 efi
drwxr-xr-x  5 root root 4.0K Jul  1 23:17 grub
drwxr-xr-x  4 root root 4.0K Feb  3 17:48 grub.bak
lrwxrwxrwx  1 root root   28 Jul  1 23:00 initrd.img -> initrd.img-5.19.0-46-generic
-rw-r--r--  1 root root 120M Jun 28 19:01 initrd.img-5.19.0-46-generic
lrwxrwxrwx  1 root root   28 Jul  1 23:00 initrd.img.old -> initrd.img-5.19.0-46-generic
drwx------  2 root root  16K Feb  1 00:40 lost+found
-rw-r--r--  1 root root 179K Feb  6  2022 memtest86+.bin
-rw-r--r--  1 root root 181K Feb  6  2022 memtest86+.elf
-rw-r--r--  1 root root 181K Feb  6  2022 memtest86+_multiboot.bin
-rw-------  1 root root 6.2M Jun 21 15:38 System.map-5.19.0-46-generic
lrwxrwxrwx  1 root root   25 Jul  1 23:00 vmlinuz -> vmlinuz-5.19.0-46-generic
-rw-------  1 root root  12M Jun 21 15:43 vmlinuz-5.19.0-46-generic
lrwxrwxrwx  1 root root   25 Jul  1 23:00 vmlinuz.old -> vmlinuz-5.19.0-46-generic

---

### Post by Bashing-om on 2023-07-02
caterhamfan; Hello

Sure one can remove - better yet copy off to a USB drive - then delete grub.bak.
However !
With only the one kernel installed I find it real strange that there are space constraints in /boot/.

Maybe we can help to see where the constraints are.
Change directory to /
```

cd /

```

Now please show us:
```

df -h
sudo du -shx * | sort -h

```

See what we learn and where we go from here.

[INDENT]gotta be a reason
[/INDENT]

---

### Post by caterhamfan on 2023-07-02
Thank you Bashing-om for your response.

Here is the output

--------------------------------------------------------
sudo du -shx * | sort -h
Filesystem                 Size  Used Avail Use% Mounted on
tmpfs                      1.6G  2.4M  1.6G   1% /run
/dev/mapper/vgubuntu-root  912G  208G  659G  24% /
tmpfs                      7.8G     0  7.8G   0% /dev/shm
tmpfs                      5.0M  4.0K  5.0M   1% /run/lock
/dev/sda2                  1.7G  152M  1.4G  10% /boot
/dev/sda1                  511M   37M  475M   8% /boot/efi
tmpfs                      1.6G  148K  1.6G   1% /run/user/1000
-----------------------------------------------------------

I'm unsure if even removing it would make a difference. Plus, I don't know how to, I can't just remove it from the /boot folder. What command could I use?

Thank you,

---

### Post by yancek on 2023-07-02
What is the exact error message you get when you to update?  Your du output shows only 8% used on the /boot partition (sda1).

---

### Post by caterhamfan on 2023-07-02
> **yancek said:**
> What is the exact error message you get when you to update?  Your du output shows only 8% used on the /boot partition (sda1).

This message.

----------------------------------------
Not enough free space
The upgrade needs a total of 1,490 M free space on disk '/boot'. Please free at least an additional 30.7 M of disk space on '/boot'. You can remove old kernels using 'sudo apt autoremove', and you could also set COMPRESS=xz in /etc/initramfs-tools/initramfs.conf to reduce the size of your initramfs.

---

### Post by Rubi1200 on 2023-07-02
What does this output show?

```
dpkg --list | grep linux-image

```

---

### Post by caterhamfan on 2023-07-03
Here it is.
It's showing kernels I thought I removed?

-------------------------

```
rc  linux-image-5.15.0-43-generic              5.15.0-43.46                                    amd64        Signed kernel image generic
rc  linux-image-5.15.0-58-generic              5.15.0-58.64                                    amd64        Signed kernel image generic
rc  linux-image-5.15.0-60-generic              5.15.0-60.66                                    amd64        Signed kernel image generic
rc  linux-image-5.19.0-32-generic              5.19.0-32.33~22.04.1                            amd64        Signed kernel image generic
rc  linux-image-5.19.0-35-generic              5.19.0-35.36~22.04.1                            amd64        Signed kernel image generic
rc  linux-image-5.19.0-38-generic              5.19.0-38.39~22.04.1                            amd64        Signed kernel image generic
rc  linux-image-5.19.0-40-generic              5.19.0-40.41~22.04.1                            amd64        Signed kernel image generic
rc  linux-image-5.19.0-41-generic              5.19.0-41.42~22.04.1                            amd64        Signed kernel image generic
rc  linux-image-5.19.0-42-generic              5.19.0-42.43~22.04.1                            amd64        Signed kernel image generic
rc  linux-image-5.19.0-43-generic              5.19.0-43.44~22.04.1                            amd64        Signed kernel image generic
ii  linux-image-5.19.0-46-generic              5.19.0-46.47~22.04.1                            amd64        Signed kernel image generic
```

---

### Post by tea for one on 2023-07-03
rc means that the kernel has been removed but configuration files are still present.
To remove these configuration files, try this:-
```
dpkg -l | awk '/^rc/{print $2}' | xargs sudo apt purge -y
```
To list installed kernels, I use this:-
```
edited@edited-22-04:~$ ls /boot | grep vmlinuz-
vmlinuz-5.19.0-43-generic
vmlinuz-5.19.0-45-generic
vmlinuz-5.19.0-46-generic
edited@edited-22-04:~$ 
```

---

### Post by caterhamfan on 2023-07-03
Fixed! After running that purge command was able to upgrade. Thanks so much!

---

### Post by ActionParsnip on 2023-07-03
Please mark as solved if the issue is resolved

---

### Post by caterhamfan on 2023-07-04
Done!

---

