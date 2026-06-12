---
title: "GParted: Unable to create ext4 parition"
date: 2014-11-06
forum: General Help
---

### Post by linuxguy2 on 2014-11-06
Hello guys! I am trying to format and partition an external drive, with no success. I have posted the details of my last two sessions with GParted, and I am hoping somebody could steer me in the right direction of what's going on here.
  Session 1:
    GParted 0.18.0 --enable-libparted-dmraid --enable-online-resize  Libparted 2.3  [TABLE]  [TR]  [TD="colspan: 2"] **Delete /dev/sdb1 (unknown, 698.64 GiB) from /dev/sdb**  00:00:00    ( SUCCESS ) [/TD]  [/TR]  [TR]  [TD]    [/TD]  [TD] [TABLE]  [TR]  [TD="colspan: 2"] calibrate /dev/sdb1  00:00:00    ( SUCCESS ) [/TD]  [/TR]  [TR]  [TD]    [/TD]  [TD] [TABLE]  [TR]  [TD="colspan: 2"] *path: /dev/sdb1 start: 2048 end: 1465147391 size: 1465145344 (698.64 GiB)* [/TD]  [/TR]  [/TABLE]  [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] delete partition  00:00:00    ( SUCCESS ) [/TD]  [/TR]  [/TABLE]  [/TD]  [/TR]  [/TABLE]  ========================================  [TABLE]  [TR]  [TD="colspan: 2"] **Create Primary Partition #1 (ext4, 698.64 GiB) on /dev/sdb**  00:01:07    ( ERROR ) [/TD]  [/TR]  [TR]  [TD]    [/TD]  [TD] [TABLE]  [TR]  [TD="colspan: 2"] create empty partition  00:00:01    ( SUCCESS ) [/TD]  [/TR]  [TR]  [TD]    [/TD]  [TD] [TABLE]  [TR]  [TD="colspan: 2"] *path: /dev/sdb1 start: 2048 end: 1465147391 size: 1465145344 (698.64 GiB)* [/TD]  [/TR]  [/TABLE]  [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] clear old file system signatures in /dev/sdb1  00:00:00    ( SUCCESS ) [/TD]  [/TR]  [TR]  [TD]    [/TD]  [TD] [TABLE]  [TR]  [TD="colspan: 2"] write 68.00 KiB of zeros at byte offset 0  00:00:00    ( SUCCESS ) [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] write 4.00 KiB of zeros at byte offset 67108864  00:00:00    ( SUCCESS ) [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] write 4.00 KiB of zeros at byte offset 274877906944  00:00:00    ( SUCCESS ) [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] write 4.00 KiB of zeros at byte offset 750154412032  00:00:00    ( SUCCESS ) [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] flush operating system cache of /dev/sdb  00:00:00    ( SUCCESS ) [/TD]  [/TR]  [/TABLE]  [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] set partition type on /dev/sdb1  00:00:00    ( SUCCESS ) [/TD]  [/TR]  [TR]  [TD]    [/TD]  [TD] [TABLE]  [TR]  [TD="colspan: 2"] *new partition type: ext4* [/TD]  [/TR]  [/TABLE]  [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] create new ext4 file system  00:01:06    ( ERROR ) [/TD]  [/TR]  [TR]  [TD]    [/TD]  [TD] [TABLE]  [TR]  [TD="colspan: 2"] ***mkfs.ext4 -L &quot;&quot; /dev/sdb1*** [/TD]  [/TR]  [TR]  [TD]    [/TD]  [TD] [TABLE]  [TR]  [TD="colspan: 2"] *Filesystem label= OS type: Linux Block size=4096 (log=2) Fragment size=4096 (log=2) Stride=0 blocks, Stripe width=0 blocks 45793280 inodes, 183143168 blocks 9157158 blocks (5.00%) reserved for the super user First data block=0 Maximum filesystem blocks=4294967296 5590 block groups 32768 blocks per group, 32768 fragments per group 8192 inodes per group Superblock backups stored on blocks:  	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,  	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,  	102400000  Allocating group tables: done                             Writing inode tables: done                             Creating journal (32768 blocks): done Writing superblocks and filesystem accounting information:  730/5590* [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] *mke2fs 1.42.9 (4-Feb-2014)  Warning, had trouble writing out superblocks.* [/TD]  [/TR]  [/TABLE]  [/TD]  [/TR]  [/TABLE]  [/TD]  [/TR]  [/TABLE]  [/TD]  [/TR]  [/TABLE]  ========================================   
 Session 2:
  GParted 0.18.0 --enable-libparted-dmraid --enable-online-resize  Libparted 2.3  [TABLE]  [TR]  [TD="colspan: 2"] **Create Primary Partition #1 (ext4, 698.64 GiB) on /dev/sdb**  00:01:32    ( ERROR ) [/TD]  [/TR]  [TR]  [TD]    [/TD]  [TD] [TABLE]  [TR]  [TD="colspan: 2"] create empty partition  00:00:00    ( SUCCESS ) [/TD]  [/TR]  [TR]  [TD]    [/TD]  [TD] [TABLE]  [TR]  [TD="colspan: 2"] *path: /dev/sdb1 start: 2048 end: 1465147391 size: 1465145344 (698.64 GiB)* [/TD]  [/TR]  [/TABLE]  [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] clear old file system signatures in /dev/sdb1  00:00:01    ( SUCCESS ) [/TD]  [/TR]  [TR]  [TD]    [/TD]  [TD] [TABLE]  [TR]  [TD="colspan: 2"] write 68.00 KiB of zeros at byte offset 0  00:00:00    ( SUCCESS ) [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] write 4.00 KiB of zeros at byte offset 67108864  00:00:00    ( SUCCESS ) [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] write 4.00 KiB of zeros at byte offset 274877906944  00:00:00    ( SUCCESS ) [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] write 4.00 KiB of zeros at byte offset 750154412032  00:00:00    ( SUCCESS ) [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] flush operating system cache of /dev/sdb  00:00:01    ( SUCCESS ) [/TD]  [/TR]  [/TABLE]  [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] set partition type on /dev/sdb1  00:00:00    ( SUCCESS ) [/TD]  [/TR]  [TR]  [TD]    [/TD]  [TD] [TABLE]  [TR]  [TD="colspan: 2"] *new partition type: ext4* [/TD]  [/TR]  [/TABLE]  [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] create new ext4 file system  00:01:31    ( ERROR ) [/TD]  [/TR]  [TR]  [TD]    [/TD]  [TD] [TABLE]  [TR]  [TD="colspan: 2"] ***mkfs.ext4 -L &quot;&quot; /dev/sdb1*** [/TD]  [/TR]  [TR]  [TD]    [/TD]  [TD] [TABLE]  [TR]  [TD="colspan: 2"] *Filesystem label= OS type: Linux Block size=4096 (log=2) Fragment size=4096 (log=2) Stride=0 blocks, Stripe width=0 blocks 45793280 inodes, 183143168 blocks 9157158 blocks (5.00%) reserved for the super user First data block=0 Maximum filesystem blocks=4294967296 5590 block groups 32768 blocks per group, 32768 fragments per group 8192 inodes per group Superblock backups stored on blocks:  	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,  	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,  	102400000  Allocating group tables: done                             Writing inode tables: done                             Creating journal (32768 blocks): done Writing superblocks and filesystem accounting information:  730/5590* [/TD]  [/TR]  [/TABLE]  [TABLE]  [TR]  [TD="colspan: 2"] *mke2fs 1.42.9 (4-Feb-2014)  Warning, had trouble writing out superblocks.* [/TD]  [/TR]  [/TABLE]  [/TD]  [/TR]  [/TABLE]  [/TD]  [/TR]  [/TABLE]  [/TD]  [/TR]  [/TABLE]  ========================================

---

### Post by Bucky Ball on 2014-11-06
Just wondering why you are not creating an EXT4 partition all in one hit? Appears as if you are creating a partition then attempting to make it EXT4. :-k Correct me if I'm misunderstanding please.

---

### Post by linuxguy2 on 2014-11-07
You're correct, Bucky Ball. Since I was already having some trouble with it, I thought maybe I should go at it one step at a time. In truth, it probably doesn't make any difference.

---

### Post by Bucky Ball on 2014-11-07
All good. Start with unallocated space. Right click the unallocated space (in Gparted I'm meaning) and give it a mountpoint name (can be anything, i.e. /MyStuff), a size (you can only get it as big as the unallocated block), and make it EXT4. That's about it. ;)

It will then take a little tweaking to make it mount on boot, if that's what you want, but if you are confident the partition is created at the end of the above procedure (you will see it there in Gparted), reboot and let's see where we're at.

If it gives an error when booting Ubuntu about having issues mounting /dev/sd**, ignore. We can fix that in the next step.

BTW, are you using the Gparted GUI or using it from a terminal? The GUI makes things a lot easier if you are unfamiliar with Linux or the terminal. Just throwin' that in.

---

### Post by gedakc on 2014-11-08
The message "*mke2fs 1.42.9 (4-Feb-2014) Warning, had trouble writing out superblocks.*" often indicates a hardware problem.  This is can be as simple as a loose cable, or as serious as a failing hard drive.

After the partition creation step fails, open a terminal window, run the **dmesg** command and check for hardware problems in the output.

You might also try installing **gsmartcontrol** and using it to check on the health of your hard drives.  I suspect that your hard drive is beginning to fail.

---

