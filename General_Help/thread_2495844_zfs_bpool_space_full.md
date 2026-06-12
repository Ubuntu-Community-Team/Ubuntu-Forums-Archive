---
title: "zfs bpool space full"
date: 2024-03-04
forum: General Help
---

### Post by detzi88 on 2024-03-04
Hi,
i use zfs with my Ubuntu 22.04 LTS. When i run `zfs list -r bpool` i get the following

```

NAME                       USED  AVAIL     REFER  MOUNTPOINT
bpool                     1.73G  20.8M       96K  /boot
bpool/BOOT                1.72G  20.8M       96K  none
bpool/BOOT/ubuntu_asenxf  1.72G  20.8M      101M  /boot

```

then `cd /boot` and `du -h` i get:
```
3,5M    ./grub/x86_64-efi
132K    ./grub/locale
2,3M    ./grub/fonts
8,2M    ./grub
3,5M    ./efi/grub/x86_64-efi
132K    ./efi/grub/locale
2,3M    ./efi/grub/fonts
8,2M    ./efi/grub
4,3M    ./efi/EFI/ubuntu
1,9M    ./efi/EFI/BOOT
6,1M    ./efi/EFI
4,0K    ./efi/System Volume Information
15M    ./efi
124M    .
```
i ran 'sudo apt autoremove'. i deleted all old kernels:

```
zfs list -t snapshot bpool
no datasets available
```

```
dpkg --list | grep linux-image
rc  linux-image-5.17.0-1035-oem                5.17.0-1035.36                          amd64        Signed kernel image oem
rc  linux-image-6.1.0-1020-oem                 6.1.0-1020.20                           amd64        Signed kernel image oem
rc  linux-image-6.1.0-1027-oem                 6.1.0-1027.27                           amd64        Signed kernel image oem
rc  linux-image-6.1.0-1028-oem                 6.1.0-1028.28                           amd64        Signed kernel image oem
rc  linux-image-6.1.0-1029-oem                 6.1.0-1029.29                           amd64        Signed kernel image oem
rc  linux-image-6.1.0-1033-oem                 6.1.0-1033.33                           amd64        Signed kernel image oem
ii  linux-image-6.1.0-1034-oem                 6.1.0-1034.34                           amd64        Signed kernel image oem
rc  linux-image-unsigned-6.1.0-1028-oem        6.1.0-1028.28                           amd64        Linux kernel image for version 6.1.0 on 64 bit x86 SMP
```

i also scrubbed the pool. But i still have a full bpool:

```
xz: (stdout): Write error: No space left on device
E: mkinitramfs failure xz --check=crc32 --threads=0 1##########.............] 
update-initramfs: failed for /boot/initrd.img-6.1.0-1034-oem with 1.
```

how can i freeup space on my bpool?

---

### Post by ActionParsnip on 2024-03-04
You can clear up with
```

dpkg -P `dpkg -l | grep ^rc | awk {'print $2'}`

```
Should get you some space back. Its old configs for removed kernels

---

### Post by detzi88 on 2024-03-04
Hey thanks for answering me. I did run the command and it seems to ave done "a lot" but the space left on bpool stays almost identical:
```
zfs list -r bpool
NAME                       USED  AVAIL     REFER  MOUNTPOINT
bpool                     1.73G  21.0M       96K  /boot
bpool/BOOT                1.72G  21.0M       96K  none
bpool/BOOT/ubuntu_asenxf  1.72G  21.0M      101M  /boot

```

---

### Post by ActionParsnip on 2024-03-04
Yeah its the old config nonsense from old packages. What is the output of
```

ls /boot

```

---

### Post by MAFoElffen on 2024-03-04
Delete/destroy your old snapshots, and remove your old kernels.

Rule of thumb:
1.) Leave only the 3 latest kernel versions. 
2.) You should need 3-5 snapshots.

If you search on my name in the forum... You will find where I helped others with this. Such at this thread: [https://ubuntuforums.org/showthread.php?t=2480236](https://ubuntuforums.org/showthread.php?t=2480236)

Did you originally install zfs-on-root as 20.04 or 22.04? That would tell me if you have 'zsys' installed and can use zsysctl... Then, if so, then you need to create a 'zyz.conf' file to change zsys'es default number of snapshots to 5 instead of it's default 20... I can provide the .conf file. It isn't there by default. If I'm not available, you can also find that by searching on my username, where I provided it to others here.

---

### Post by detzi88 on 2024-03-05
> **ActionParsnip said:**
> Yeah its the old config nonsense from old packages. What is the output of
```

ls /boot

```

The output is:
```

ls -la --block-size=M /boot/
total 102M
drwxr-xr-x  4 root root  1M Mär  5 07:48 .
drwxr-xr-x 19 root root  1M Feb  9 09:51 ..
-rw-r--r--  1 root root  1M Feb  5 16:55 config-6.1.0-1034-oem
drwxr-xr-x  5 root root  1M Jan  1  1970 efi
drwxr-xr-x  5 root root  1M Mär  4 13:32 grub
lrwxrwxrwx  1 root root  1M Feb 23 07:26 initrd.img -> initrd.img-6.1.0-1034-oem
-rw-r--r--  1 root root 87M Feb 29 12:42 initrd.img-6.1.0-1034-oem
lrwxrwxrwx  1 root root  1M Mär  2 06:50 initrd.img.old -> initrd.img-6.1.0-1034-oem
-rw-r--r--  1 root root  1M Feb  6  2022 memtest86+.bin
-rw-r--r--  1 root root  1M Feb  6  2022 memtest86+.elf
-rw-r--r--  1 root root  1M Feb  6  2022 memtest86+_multiboot.bin
-rw-------  1 root root  6M Feb  5 16:55 System.map-6.1.0-1034-oem
lrwxrwxrwx  1 root root  1M Feb 23 07:26 vmlinuz -> vmlinuz-6.1.0-1034-oem
-rw-------  1 root root 13M Feb  5 17:03 vmlinuz-6.1.0-1034-oem
lrwxrwxrwx  1 root root  1M Mär  2 06:50 vmlinuz.old -> vmlinuz-6.1.0-1034-oem

```

---

### Post by detzi88 on 2024-03-05
> **MAFoElffen said:**
> Delete/destroy your old snapshots, and remove your old kernels.

Rule of thumb:
1.) Leave only the 3 latest kernel versions. 
2.) You should need 3-5 snapshots.

If you search on my name in the forum... You will find where I helped others with this. Such at this thread: [https://ubuntuforums.org/showthread.php?t=2480236](https://ubuntuforums.org/showthread.php?t=2480236)

Did you originally install zfs-on-root as 20.04 or 22.04? That would tell me if you have 'zsys' installed and can use zsysctl... Then, if so, then you need to create a 'zyz.conf' file to change zsys'es default number of snapshots to 5 instead of it's default 20... I can provide the .conf file. It isn't there by default. If I'm not available, you can also find that by searching on my username, where I provided it to others here.


I installed zfs as part of the Ubuntu 22.04 LTS installer. Zsys was not installed but i installed it and tried a suggestion from here: [https://github.com/ubuntu/zsys/issues/155](https://github.com/ubuntu/zsys/issues/155). That did not work so i removed zsys again. I also disabled snapshoting on bpool for now and removed all old snapshots so that shouldn't be the issue.
```

zfs list -t snapshot bpool
no datasets available

```
I have also already removed all but the current kernel version.

---

### Post by MAFoElffen on 2024-03-05
By what you posted you only have 118M used in 2GB... You have freed up quite a bit of room.

How is it that it that it still shows 1.7GB being used? Or is that an earlier post? (before freeing up space?)

---

### Post by detzi88 on 2024-03-05
That is exactly the issue, not much has changed since my first post. There are still only 120MB worth of files shown but the drive is still somehow using 1.7GB leaving only 20MB of free space available.

---

### Post by detzi88 on 2024-03-06
TLDR: Use "zfs list -o space -r bpool" to check for snapshots.
So it turns out that:
```
zfs list -t snapshot bpool
no datasets available

```
only shows the snapshot for that specific dataset, not any one below it.
```
zfs list -o space -r bpool
NAME                      AVAIL   USED  USEDSNAP  USEDDS  USEDREFRESERV  USEDCHILD
bpool                     21.1M  1.73G        0B     96K             0B      1.73G
bpool/BOOT                21.1M  1.72G        0B     96K             0B      1.72G
bpool/BOOT/ubuntu_asenxf  21.1M  1.72G     1.62G    101M             0B         0B
```
reveals that still 1.6GB of snapshots are available, which are located in "bpool/BOOT" and "bpool/BOOT/ubuntu_asenxf" (mainly the latter).
i removed them with:
```

sudo -i
zfs list -H -o name -t snapshot bpool/BOOT| xargs -n1 zfs destroy
zfs list -H -o name -t snapshot bpool/BOOT/ubuntu_asenxf| xargs -n1 zfs destroy

```
now i get
```

zfs list -o space -r bpool
NAME                      AVAIL   USED  USEDSNAP  USEDDS  USEDREFRESERV  USEDCHILD
bpool                     1.65G   104M        0B     96K             0B       103M
bpool/BOOT                1.65G   101M        0B     96K             0B       101M
bpool/BOOT/ubuntu_asenxf  1.65G   101M        0B    101M             0B         0B

```
case closed thanks for assisting.

---

### Post by MAFoElffen on 2024-03-07
You are welcome. Happy that it is working for you now.

In this is "Solved", we are responsible for closing out our own threads that we start... Please visit the "Thread Tools" link and mark your thread as "Solve" so that other with similar problem can find what worked for you.

---

