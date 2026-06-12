---
title: "my hd died?"
date: 2014-11-21
forum: General Help
---

### Post by hsaptus on 2014-11-21
Evenin'
I am not sure what happen in here but this is what i have:
> sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d4cd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     9766911     4882432   82  Linux swap / Solaris
/dev/sda2         9768958   976771071   483501057    5  Extended
/dev/sda5         9768960   976771071   483501056   83  Linux



> df -h
df: `/live/rofs/filesystem.squashfs': No such file or directory
df: `/root/.gvfs': Permission denied
Filesystem      Size  Used Avail Use% Mounted on
rootfs          1.8G   41M  1.7G   3% /
udev             10M     0   10M   0% /dev
tmpfs           355M  656K  355M   1% /run
/dev/sr0        771M  771M     0 100% /live/image
tmpfs           1.8G   41M  1.7G   3% /live/overlay
tmpfs           1.8G   41M  1.7G   3% /live/overlay
aufs            1.8G   41M  1.7G   3% /
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           710M   92K  710M   1% /run/shm



[ATTACH=CONFIG]258111[/ATTACH]

and I cant get to that drive.

using a live distro to try to recover it.
Any ideas?
tia,
h.

---

### Post by pqwoerituytrueiwoq on 2014-11-21
open gparted right click it and click repair, cross fingers

---

### Post by Bashing-om on 2014-11-21
hsaptus; Hello;

+1 What pqwoerituytrueiwoq said;
Might be able to fix this install; What is the boot process like ( what happens !).
If you depress the right shift key as soon as bios screen clears, do you get a grub boot menu ?
Yes ? What results when choosing to boot an older kernel from the "advanced options" menu ?

One can mount the installed file system from the liveDVD, have a look around -  and pull your personal files off. It is always a great idea to keep good backups !

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]it's fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hsaptus on 2014-11-21
Yes, I get the grub menu, but nothing happens after I try to load the kernel. Not even with an older kernel. And I cant mount it with a live distro also.

---

### Post by Bashing-om on 2014-11-21
hsaptus; Well !

What results from the liveDVD -> terminal:
terminal commands:
```

sudo mkdir /mnt/work
sudo mount dev/sda5 /mnt/work
ls -al /mnt/work
ls -al /mnt/work/home
sudo umount /mnt/work

```

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Pending this, is what we do next.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by hsaptus on 2014-11-21
Thank you for your help.
I did try that already. I get this:
> sudo mount /dev/sda5 /mnt/work
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try


Also did that:

> [ 6957.826330] JBD2: Failed to read block at offset 2170
[ 6957.826331] JBD2: IO error -5 recovering block 2170 in log
[ 6957.826332] JBD2: Failed to read block at offset 2171
[ 6957.826334] JBD2: IO error -5 recovering block 2171 in log
[ 6957.826335] JBD2: Failed to read block at offset 2172
[ 6957.826336] JBD2: IO error -5 recovering block 2172 in log
[ 6957.826338] JBD2: Failed to read block at offset 2173
[ 6957.826339] JBD2: IO error -5 recovering block 2173 in log
[ 6959.293337] JBD2: recovery failed
[ 6959.293342] EXT4-fs (sda5): error loading journal


I also did try:

>  sudo fsck /dev/sda5
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
/dev/sda5: recovering journal
Error reading block 60328034 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? no
/dev/sda5: Attempt to read block from filesystem resulted in short read while reading block 60328034

JBD: Failed to read block at offset 2146
JBD: IO error -5 recovering block 2146 in log
fsck.ext4: Bad magic number in super-block while trying to re-open /dev/sda5
Signal (11) SIGSEGV si_code=SEGV_MAPERR fault addr=0x61
fsck.ext4[0x80719c6]
[0xb7762410]
/lib/i386-linux-gnu/libext2fs.so.2(ext2fs_mmp_stop+0x27)[0xb772e777]
fsck.ext4(fatal_error+0x4e)[0x806817e]
fsck.ext4(e2fsck_run_ext3_journal+0x316)[0x8067656]
fsck.ext4(main+0x5dc)[0x805032c]
/lib/i386-linux-gnu/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0xb757de46]
fsck.ext4[0x8052e0d]
crunchbang@crunchbang:~$ sudo fsck -a /dev/sda5
fsck from util-linux 2.20.1
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda5
/dev/sda5: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>



---

### Post by Bashing-om on 2014-11-21
hsaptus; Yuk;

Does not look good for the home team .
OK, what does the SMART test from 'disk utility' reveal about the overall health of the drive ?

If the disk is in good shape, take fsck's advise and spare off the super block:
Additional instruction:
[http://ubuntuforums.org/showthread.php?t=2177756](http://ubuntuforums.org/showthread.php?t=2177756)
courtesy of slickymaster .

[INDENT][INDENT]maybe yes
[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hsaptus on 2014-11-21
OMG!!!

> sudo mke2fs -n /dev/sda5
mke2fs 1.42.5 (29-Jul-2012)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
30220288 inodes, 120875264 blocks
6043763 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
3689 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000


And after a lot of typing...

> 
crunchbang@crunchbang:~$ sudo mount /dev/sda5 /mnt/work
crunchbang@crunchbang:~$ df -h
df: `/live/rofs/filesystem.squashfs': No such file or directory
df: `/root/.gvfs': Permission denied
Filesystem      Size  Used Avail Use% Mounted on
rootfs          1.8G  295M  1.5G  17% /
udev             10M     0   10M   0% /dev
tmpfs           355M  672K  355M   1% /run
/dev/sr0        771M  771M     0 100% /live/image
tmpfs           1.8G  295M  1.5G  17% /live/overlay
tmpfs           1.8G  295M  1.5G  17% /live/overlay
aufs            1.8G  295M  1.5G  17% /
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           710M   92K  710M   1% /run/shm
/dev/sdc         64M   38M   27M  60% /media/40A1-0001
/dev/sda5       454G  199M  431G   1% /mnt/work


dammit!!! It-s mounted! Thank you mate!!! That was awesome! I just hope It will mount after the reboot... Going to make some backups first! :P

---

### Post by Bashing-om on 2014-11-21
hsaptus; Hey;

Fingers crossed, good things do happen.

Keep us informed.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]it's fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

