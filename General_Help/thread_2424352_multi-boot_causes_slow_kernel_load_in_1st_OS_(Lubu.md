---
title: "multi-boot causes slow kernel load in 1st OS (Lubuntu) - reason: swap formatting"
date: 2019-08-07
forum: General Help
---

### Post by &amp;wP*!) on 2019-08-07
Creating a 2nd btrfs partition causes slower kernel loading in Lubuntu.

**Setup**
Lubuntu 19.04 has been installed on /dev/sda5 (btrfs) with the following entries in **/etc/fstab** in this partition:
```
UUID=e176f344-e020-435f-9097-0a5c719aab69 /              btrfs   subvol=@,defaults,noatime,space_cache,autodefrag,compress=lzo 0 1
UUID=e176f344-e020-435f-9097-0a5c719aab69 /home          btrfs   subvol=@home,defaults,noatime,space_cache,autodefrag,compress=lzo 0 2
```
So far boot time was below 10 seconds. Below is the dmesg from a boot of Lubuntu without /dev/sda6 on 23rd of July:
```
$ journalctl -b -42 --dmesg -o short-monotonic
-- Logs begin at Tue 2019-07-23 14:38:30 CEST, end at Wed 2019-08-07 10:20:40 CEST. --
[    0.000000] host-lubuntu kernel: Linux version 5.0.0-13-generic (buildd@lcy01-amd64-020) (gcc version 8.3.0 (Ubuntu 8.3.0-6ubuntu1))
[    0.000000] host-lubuntu kernel: Command line: BOOT_IMAGE=/@/boot/vmlinuz-5.0.0-13-generic root=UUID=e176f344-e020-435f-9097-0a5c719
...
[    3.852200] host-lubuntu kernel: Btrfs loaded, crc32c=crc32c-intel
[    3.918317] host-lubuntu kernel: BTRFS: device fsid e176f344-e020-435f-9097-0a5c719aab69 devid 1 transid 48 /dev/sda5
[    3.965227] host-lubuntu kernel: BTRFS info (device sda5): disk space caching is enabled
[    3.965228] host-lubuntu kernel: BTRFS info (device sda5): has skinny extents
[    3.967232] host-lubuntu kernel: BTRFS info (device sda5): enabling ssd optimizations
```
Arch Linux has been installed on /dev/sda6 (btrfs) with the following entry in **/etc/fstab** in this partition:
```
UUID=38d0a8a6-4a6e-49d9-8db9-dac73b56d3aa	/         	btrfs     	rw,relatime,ssd,space_cache,subvolid=5,subvol=/	0 0
```
The partition /dev/sda6 of Arch Linux was created with **mkfs.btrfs -L ARCH /dev/sda6** in Arch Linux installation. This partition has not been mounted in /etc/fstab of Lubuntu (/dev/sda5).

Having this, **systemd** in Lubuntu shows kernel load takes 35 seconds:
```
$ systemd-analyze
Startup finished in 4.573s (firmware) + 1.577s (loader) + **35.109s (kernel)** + 12.523s (userspace) = 53.784s 
graphical.target reached after 12.354s in userspace
```
**Observation**
**dmesg** in Lubuntu shows that during the Lubuntu load BTRFS checks on /dev/sda5 now takes >30 seconds:
```
[    0.000000] Linux version 5.0.0-23-generic (buildd@lcy01-amd64-017) (gcc version 8.3.0 (Ubuntu 8.3.0-6ubuntu1)) #24-Ubuntu SMP Mon J
ul 29 15:36:44 UTC 2019 (Ubuntu 5.0.0-23.24-generic 5.0.15)
[    0.000000] Command line: BOOT_IMAGE=/@/boot/vmlinuz-5.0.0-23-generic root=UUID=e176f344-e020-435f-9097-0a5c719aab69 ro rootflags=su
bvol=@ quiet splash resume=UUID=73f67efb-e185-470a-83f2-07d4de9895d3 vt.handoff=1
...
[    3.885967] Btrfs loaded, crc32c=crc32c-intel
[    3.919213] BTRFS: device label ARCH devid 1 transid 100 /dev/sda6
[    3.919370] BTRFS: device fsid e176f344-e020-435f-9097-0a5c719aab69 devid 1 transid 10509 /dev/sda5
[   34.955142] BTRFS info (device sda5): disk space caching is enabled
[   34.955143] BTRFS info (device sda5): has skinny extents
[   34.958767] BTRFS info (device sda5): enabling ssd optimizations
```
All UUIDs were checked, all of them seem to be correct:```

$ lsblk --output NAME,FSTYPE,UUID
NAME   FSTYPE UUID
sda           
&#9500;&#9472;sda1 vfat   E0CB-576D
&#9500;&#9472;sda2 swap   da22369f-2206-4796-b046-897a03bc81ee
&#9500;&#9472;sda3        
&#9500;&#9472;sda4 ext4   ba29dceb-09c9-4f23-9d8d-174ddaff4764
&#9500;&#9472;sda5 btrfs  e176f344-e020-435f-9097-0a5c719aab69
&#9492;&#9472;sda6 btrfs  38d0a8a6-4a6e-49d9-8db9-dac73b56d3aa
```
The kernel version of Lubuntu now is newer than the one when /dev/sda6 was not  created. Lubuntu system is up-to-date as of now.
**Question:** What is the reason of this slow kernel load?
**Question:** Could be the reason the newer kernel in Lubuntu is slower?
**Question:** Is there a way to speed it up?

**Update - I suspect the correctness of RESUME during boot. **
In the latter boot of Lubuntu, where Arch + Lubuntu are installed, the Boot Image command has RESUME=UUID=73f67efb-e185-470a-83f2-07d4de9895d3 which doesn't exit. 
I have remembered that after having installed Lubuntu (and created its swap), I had re-created swap partition with **mkswap** during Arch Installation (unknowingly).
Recreating the swap causes UUID change, so far as I know.
However update-initramfs -u of Lubuntu insists on not updating this UUID.  /etc/initramfs-tools/conf.d/ is also empty. /etc/default/grub was corrected, but boot image insists on taking a wrong UUID.
Analysis ongoing.  Any help is appreciated though.

**Update: Reason found: reformatting swap for Arch Linux, which was formatted during Lubuntu, causes longer kernel boot time. ** My assumption above is correct. It is not related to BTRFS plugin/driver. It is related to RESUME parameter in **/etc/default/grub** of Lubuntu.
This is fixed in Lubuntu by
[LIST=1]
[*]Update RESUME parameter of GRUB_CMDLINE_LINUX_DEFAULT in **/etc/default/grub** to the actual UUID value of swap 
[*]Create initramfs by **sudo update-initramfs -u** - updates only the last installed kernel 
[*]Update GRUB by **sudo update-grub**
[*]Reboot
[/LIST]
Now systemd shows faster boot of Lubuntu kernel:
```
$ systemd-analyze 
Startup finished in 3.271s (firmware) + 2.166s (loader) + 3.970s (kernel) + 11.859s (userspace) = 21.267s 
graphical.target reached after 11.755s in userspace
```

I set this thread to SOLVED.

---

### Post by oldfred on 2019-08-07
The resume is not in grub but this:

```
fred@bionic-z97:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=a7750d57-5381-421b-82fa-b53194ab45c2

```
 And you normally have to update UUID in fstab of any other install if swap was reformatted with second/third install. 

I stopped using swap partition during install, but my older installs still use it. I have it use swap file, by clicking on every swap and saying not to use during new install.

---

### Post by &amp;wP*!) on 2019-08-07
> **oldfred said:**
> The resume is not in grub but this:

```
fred@bionic-z97:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=a7750d57-5381-421b-82fa-b53194ab45c2

```
 And you normally have to update UUID in fstab of any other install if swap was reformatted with second/third install. 

As I have written in the OP, /etc/initramfs-tools/conf.d/ is empty. I could have created a file with the content you proposed (same solution is mentioned a lot on web, I know). As I have written in the OP, It seems the RESUME parameter of GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub achieves the same result. I have not used your solution. I know yours also work. My solution fixed the problem.
> **oldfred said:**
> I stopped using swap partition during install, but my older installs still use it. I have it use swap file, by clicking on every swap and saying not to use during new install.
I have a dual-boot computer. Both Linux Operating systems use the same swap. A swap file could be shared among both OSes as well - this file must reside in a partition anyway. Therefore I directly used partition for swap instead of a common swap file in a partition.

---

