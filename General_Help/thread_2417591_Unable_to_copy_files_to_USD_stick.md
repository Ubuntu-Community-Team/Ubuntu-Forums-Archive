---
title: "Unable to copy files to USD stick"
date: 2019-04-24
forum: General Help
---

### Post by satimis on 2019-04-24
Hi all,

It is strange to me that I can't copy files to USB stick.  It is mounted automatically when I plug it to the computer.

&#10219; df -hT```

Filesystem                  Type      Size  Used Avail Use% Mounted on
udev                        devtmpfs   16G     0   16G   0% /dev
tmpfs                       tmpfs     3.2G  9.4M  3.2G   1% /run
/dev/mapper/ubuntu--vg-root ext4      1.8T  912G  828G  53% /
tmpfs                       tmpfs      16G  390M   16G   3% /dev/shm
tmpfs                       tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                       tmpfs      16G     0   16G   0% /sys/fs/cgroup
/dev/sda1                   ext2      720M  139M  545M  21% /boot
tmpfs                       tmpfs     3.2G  112K  3.2G   1% /run/user/1000
/dev/sdb1                   ext4      1.8T  400G  1.4T  23% /media/satimis/eee0a8e0-4ac5-433e-b6e0-9cbf67916666
/dev/sdc                    ext4      1.4T  775G  531G  60% /media/satimis/datapartition
/dev/sdd                    ext4      7.3G   17M  6.9G   1% /media/satimis/9d944117-43a2-4b43-a058-1ccc813aae92

```

&#10219; sudo blkid```

/dev/sda1: UUID="894ba3e3-6129-4782-89d1-2b861ccc4969" TYPE="ext2" PARTUUID="429ca318-01"
/dev/sda5: UUID="eTZ5fE-sQuc-t9RB-Rfc8-7W1H-o1Hn-Yq6ZOa" TYPE="LVM2_member" PARTUUID="429ca318-05"
/dev/sdb1: UUID="eee0a8e0-4ac5-433e-b6e0-9cbf67916666" TYPE="ext4" PARTUUID="09ab06ac-01"
/dev/mapper/ubuntu--vg-root: UUID="9ccf8449-617f-4962-aaf3-060377e9ce12" TYPE="ext4"
/dev/sdc: LABEL="datapartition" UUID="666e16be-82e0-48c6-8ac5-eaa8f0f7b067" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="e4e0ba94-51d3-4f02-90c2-c40e4ff08475" TYPE="swap"
/dev/sdd: UUID="9d944117-43a2-4b43-a058-1ccc813aae92" TYPE="ext4"

```

&#10219; ls -al /dev/sdd```
 
brw-rw---- 1 root disk 8, 48 Apr 25 07:58 /dev/sdd

```

Ran;
&#10219; sudo chown satimis:satimis /dev/sdd 
&#10219; ls -al /dev/sdd ```

brw-rw---- 1 satimis satimis 8, 48 Apr 25 08:09 /dev/sdd

```

Still I couldn't copy files on it

Replugin it and it is mounted automatically

&#10219; ls -al /dev/sdd ```

brw-rw---- 1 root disk 8, 48 Apr 25 08:14 /dev/sdd

```
It is very strange.  It changes back to "root disk 8

Please help.  Thanks in advance

Regards
satimis

---

### Post by #&amp;thj^% on 2019-04-24
I always with an ext4 format use:
```
sudo fdisk -l
```

will tell you what's mounted. Then run:
```
sudo chmod 666 /dev/sdd
```
That will allow you to read and write to the device.

---

### Post by satimis on 2019-04-24
> **1fallen said:**
> I always with an ext4 format use:
```
sudo fdisk -l
```

will tell you what's mounted. Then run:
```
sudo chmod 666 /dev/sdd
```
That will allow you to read and write to the device.
Thanks for your advice.

I'm sure /dev/sdd is USB stick.  Before plugin /dev/sdd is NOT shown on running "sudo fdisk -l"

Also I tried 777 before but still failed unable copying files to USB stick

Performed following steps;
&#10219; sudo chmod 666 /dev/sdd 
&#10219; ls -al /dev/sdd ```

brw-rw-rw- 1 root disk 8, 48 Apr 25 09:04 /dev/sdd

```

Still unable to copy files to USB stick

&#10219; sudo chown satimis:satimis /dev/sdd 
&#10219; ls -al /dev/sdd ```

brw-rw-rw- 1 satimis satimis 8, 48 Apr 25 09:04 /dev/sdd

```

Still unable to copy files to USB Stick


Edit-1
=====
&#10219; sudo fdisk -l```

.....
.....
Disk /dev/sdd: 7.5 GiB, 8053063680 bytes, 15728640 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

Edit-2
====
Problem solved.  I forgot to format the USB stick

Now I can copy files to it.

&#10219; ls -al /dev/sdd ```

brw-rw---- 1 root disk 8, 48 Apr 25 10:40 /dev/sdd

```

It is not necessary to make any change here.


Regards
satimis

---

