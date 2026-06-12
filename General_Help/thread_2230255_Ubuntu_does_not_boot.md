---
title: "Ubuntu does not boot"
date: 2014-06-18
forum: General Help
---

### Post by lunaservant on 2014-06-18
I do not shut my laptop down very often but every few days I will turn it off overnight while I'm sleeping.  Last night I turned it off and when I turned it on this morning it would not boot.  After fiddling around a bit I discovered it flashes an error that is only on screen for less than a second while the Ubuntu splash screen is up.  The Ubuntu splash screen itself is only on screen for about 2 seconds before it goes to a black screen and stays there until i turn the computer off.  I have never had this issue before.  I don't know what the error says because it's not on the screen long enough.

I can boot Ubuntu into recovery mode but I am unable to turn on networking to check for broken packages.  I was also able to boot the Ubuntu live CD with no trouble.

I am using Ubuntu 14 64-bit.  inxi -fxz is below:

```
ubuntu@ubuntu:~$ inxi -fxz**CPU**:       Quad core AMD A4-5000 APU with Radeon HD Graphics (-MCP-) **cache:** 8192 KB **bmips**: 11977.6 
          ** Clock Speeds:** **1**: 800.00 MHz **2**: 800.00 MHz **3**: 800.00 MHz **4:** 1500.00 MHz
          ** CPU Flag**s: 3dnowprefetch abm aes aperfmperf apic arat avx bmi1 clflush cmov cmp_legacy 
           constant_tsc cr8_legacy cx16 cx8 de decodeassists eagerfpu extapic extd_apicid f16c flushbyasid 
           fpu fxsr fxsr_opt ht hw_pstate ibs lahf_lm lbrv lm mca mce misalignsse mmx mmxext monitor 
           movbe msr mtrr nonstop_tsc nopl npt nrip_save nx osvw pae pat pausefilter pclmulqdq pdpe1gb 
           perfctr_l2 perfctr_nb pfthreshold pge pni popcnt proc_feedback pse pse36 rdtscp rep_good 
           sep skinit sse sse2 sse4_1 sse4_2 sse4a ssse3 svm svm_lock syscall topoext tsc tsc_scale 
           vme wdt xsave xsaveopt 

```

if anybody has any idea how to fix this without me having to reinstall Ubuntu it would be a great help.  If there is no way to fix it then please tell me that too

---

### Post by ajgreeny on 2014-06-18
It may be worth booting to your live system then running ```
sudo e2fsck -f /dev/sda1
```assuming sda1 is your Ubuntu root partition.

That may possibly find some filesystem problems and report them to you as errors.  Come back again and we can try to help you if there are errors showing up.

You could use that command with the options **-f -y** rather than just **-f**, the extra **-y** meaning "assume yes to repair errors" but I prefer to make that choice after running without that option first.

---

### Post by lunaservant on 2014-06-18
thank you for helping me.  here is the outcome of the code you gave:

```
ubuntu@ubuntu:~$ sudo e2fsck -f /dev/sda3
e2fsck 1.42.9 (4-Feb-2014)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda3


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

```

/dev/sda3 is my main partition

---

### Post by oldfred on 2014-06-18
I am surprised you can boot recovery with major partition issues. Or are you mounting a separate /home or other partitions and those are really the one's needing fsck?

Post this 
sudo parted -l

And as suggested in error, you can try backup superblocks.

 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by lunaservant on 2014-06-18
the partitions were the default when I installed Ubuntu

```
ubuntu@ubuntu:~$ sudo parted -lModel: ATA HGST HTS545050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End    Size   File system  Name  Flags
 1      1049kB  538MB  537MB  fat32              boot
 2      538MB   794MB  256MB  ext2
 3      794MB   500GB  499GB                     lvm




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 7986MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0.00B  7986MB  7986MB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 479GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  479GB  479GB  ext4




Model: MATSHITA DVD-RAM UJ8C2 S (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac


Number  Start   End     Size    File system  Name   Flags
 1      8192B   24.6kB  16.4kB               Apple
 2      4002MB  4012MB  9568kB               EFI



```

---

### Post by oldfred on 2014-06-18
I do not know LVM, but generally you have to use LVM tools not standard partition tools with LVM.

When running fsck, you probably have to mount LVM and only run it inside the LVM?

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by lunaservant on 2014-06-18
hmm it seems like i'm going to have to reinstall ubuntu, this time without using lvm.  I only used it because during setup it said it was easier to manage but I found it to be more complex than it needed to be when I tried to change around some partitions a few weeks ago.  well thank you your help.

---

