---
title: "Unable to boot to Trusty Tahr after Lubuntu install"
date: 2014-05-27
forum: General Help
---

### Post by bigonegotaway2 on 2014-05-27
UPDATE >>>>> I think I solved the mystery. I just used Gparted and looked at my partitions. I have an old 60gb drive that showed one large partition of about 56gb and two smaller- each 2.1gb. What appears to have happened is Lubuntu overwrote Trusty due to my lack of experience with a REAL OS - Linux and years of relying on MS to do all my thinking for me. I'll go back and create partitions then put Trusty on one and Lubuntu on the other and I'd be willing to bet it will then work fine. Sorry I didn't think of this before posting. I'm even more comitted to Linux now than before-it's the thinking persons OS! Sorry to have been a bother.

Hi all...I just did a fresh install of Trusty and then installed Lubuntu. Before when using Ubuntu- (Precise), I was able to select which distro I wanted to run at boot up- (Precise or Lubuntu). The option to choose between the two- (Trusty or Lubuntu) doesn't seem to be available now with Trusty. Every boot now is always into Lubuntu. Anything I'm overlooking? Thanks in advance for any help.

---

### Post by sudodus on 2014-05-27
Welcome to the Ubuntu Forums :-)

Please post the output of the following commands in a terminal window.

```
sudo parted -l
```

```
df
```

It will show the partitions. If it is not clear enough, you can get Boot-Repair and run Boot-Info

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by LastDino on 2014-05-27
Bit more info would help, for example on which partitions these two OS are installed and where is boot flag. 



Try;
```
 sudo os-prober /dev/sdax
```

X is where your Trusty is installed. Ex: Sda3 
You can check that out in gparted.

The try;
```
sudo update-grub
```

---

### Post by bigonegotaway2 on 2014-05-27
```
Model: ATA WDC WD600BB-75CA (scsi)
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  57.9GB  57.9GB  primary   ext4            boot
 2      57.9GB  60.0GB  2144MB  extended
 5      57.9GB  60.0GB  2144MB  logical   linux-swap(v1)


Model: A-DATA USB Flash Drive (scsi)
Disk /dev/sdb: 4058MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  4058MB  4058MB  primary  fat32        boot

```

```
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1       55479356 4433216  48204900   9% /
none                   4       0         4   0% /sys/fs/cgroup
udev             1022032       4   1022028   1% /dev
tmpfs             206320    1036    205284   1% /run
none                5120       0      5120   0% /run/lock
none             1031584      76   1031508   1% /run/shm
none              102400      24    102376   1% /run/user
/dev/sdb1        3955120 3711164    243956  94% /media/user/A-DATA UFD
```

---

### Post by bigonegotaway2 on 2014-05-27
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by sudodus on 2014-05-28
Your only linux partition, which is also the active root partition, is **/dev/sda1**.

There is also an extended partition containing the swap partition. So either you were overwriting Ubuntu when you installed Lubuntu, or you installed Lubuntu Desktop into the Ubuntu system. Anyway, you have only one system installed in the internal drive **/dev/sda**.

How did you install Lubuntu?

- from the install CD/DVD/USB drive or

- running ```
sudo apt-get install lubuntu-desktop
``` from inside Ubuntu

---

### Post by LastDino on 2014-05-28
+1 to what sudo has said, I think you installed Lubuntu on Thar partition, so it has been over written.

---

### Post by Leviata on 2014-05-28
Ow I've this problem about 3.13.0-27-generic
[http://ubuntuforums.org/showthread.php?t=2226385](http://ubuntuforums.org/showthread.php?t=2226385)
is that that same problem?

---

