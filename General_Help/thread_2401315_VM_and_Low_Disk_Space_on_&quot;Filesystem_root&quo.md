---
title: "VM and Low Disk Space on &quot;Filesystem root&quot;"
date: 2018-09-16
forum: General Help
---

### Post by webmanoffesto on 2018-09-16
I have an Ubuntu laptop running Ubuntu 16.04. I also have Oracle Virtual Box running. Now I'm getting this Low Disk Space error message and it's hard for me to decode the output below because (as a result of the VM?) it looks very unfamiliar to me. How can I resolve this problem?


```

tom@tom-HP-ProBook-450-G3:~$ sudo du -hs /*
[sudo] password for tom: 
13M    /bin
402M    /boot
4.0K    /cdrom
472K    /dev
15M    /etc
484G    /home
0    /initrd.img
0    /initrd.img.old
1.6G    /lib
3.9M    /lib32
4.0K    /lib64
16K    /lost+found
12K    /media
4.0K    /mnt
528M    /opt
du: cannot access '/proc/5165/task/5165/fd/4': No such file or directory
du: cannot access '/proc/5165/task/5165/fdinfo/4': No such file or directory
du: cannot access '/proc/5165/fd/3': No such file or directory
du: cannot access '/proc/5165/fdinfo/3': No such file or directory
0    /proc
1.4M    /root
du: cannot access '/run/user/1000/gvfs': Permission denied
18M    /run
11M    /sbin
13G    /snap
4.0K    /srv
0    /sys
3.4M    /tmp
8.3G    /usr
5.9G    /var
0    /vmlinuz
0    /vmlinuz.old
tom@tom-HP-ProBook-450-G3:~$ df -Th 
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.8G     0  7.8G   0% /dev
tmpfs          tmpfs     1.6G   18M  1.6G   2% /run
/dev/sda1      ext4       20G   17G  1.4G  93% /
tmpfs          tmpfs     7.8G   18M  7.8G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/loop2     squashfs   87M   87M     0 100% /snap/core/5145
/dev/loop3     squashfs  198M  198M     0 100% /snap/vlc/365
/dev/loop4     squashfs  196M  196M     0 100% /snap/vlc/555
/dev/loop5     squashfs  116M  116M     0 100% /snap/easy-disk-cleaner/4
/dev/loop6     squashfs  512K  512K     0 100% /snap/ufw/14
/dev/loop8     squashfs  181M  181M     0 100% /snap/vlc/190
/dev/loop7     squashfs   87M   87M     0 100% /snap/core/4917
/dev/loop10    squashfs  835M  835M     0 100% /snap/0ad/13
/dev/loop9     squashfs  835M  835M     0 100% /snap/0ad/18
/dev/loop0     squashfs   88M   88M     0 100% /snap/core/5328
/dev/loop1     squashfs  908M  908M     0 100% /snap/0ad/30
/dev/loop11    squashfs  101M  101M     0 100% /snap/easy-disk-cleaner/18
/dev/loop12    squashfs  222M  222M     0 100% /snap/freecad/4
/dev/loop13    squashfs  768K  768K     0 100% /snap/ufw/95
/dev/sda2      ext4      867G  485G  339G  59% /home
tmpfs          tmpfs     1.6G   12K  1.6G   1% /run/user/121
tmpfs          tmpfs     1.6G   32K  1.6G   1% /run/user/1000
tom@tom-HP-ProBook-450-G3:~$ sudo fdsik -l
sudo: fdsik: command not found
tom@tom-HP-ProBook-450-G3:~$ fdisk


Usage:
 fdisk [options] <disk>      change partition table
 fdisk [options] -l [<disk>] list partition table(s)


Display or manipulate a disk partition table.


Options:
 -b, --sector-size <size>      physical and logical sector size
 -B, --protect-boot            don't erase bootbits when create a new label
 -c, --compatibility[=<mode>]  mode is 'dos' or 'nondos' (default)
 -L, --color[=<when>]          colorize output (auto, always or never)
                                 colors are enabled by default
 -l, --list                    display partitions end exit
 -o, --output <list>           output columns
 -t, --type <type>             recognize specified partition table type only
 -u, --units[=<unit>]          display units: 'cylinders' or 'sectors' (default)
 -s, --getsz                   display device size in 512-byte sectors [DEPRECATED]
     --bytes                   print SIZE in bytes rather than in human readable format


 -C, --cylinders <number>      specify the number of cylinders
 -H, --heads <number>          specify the number of heads
 -S, --sectors <number>        specify the number of sectors per track


 -h, --help     display this help and exit
 -V, --version  output version information and exit


Available columns (for -o):
 gpt: Device Start End Sectors Size Type Type-UUID Attrs Name UUID
 dos: Device Start End Sectors Cylinders Size Type Id Attrs Boot End-C/H/S
      Start-C/H/S
 bsd: Slice Start End Sectors Cylinders Size Type Bsize Cpg Fsize
 sgi: Device Start End Sectors Cylinders Size Type Id Attrs
 sun: Device Start End Sectors Cylinders Size Type Id Flags


For more details see fdisk(8).
tom@tom-HP-ProBook-450-G3:~$ sudo fdisk -l
Disk /dev/loop0: 87.9 MiB, 92164096 bytes, 180008 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 908 MiB, 952107008 bytes, 1859584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 87 MiB, 91160576 bytes, 178048 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 198 MiB, 207585280 bytes, 405440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 195.2 MiB, 204644352 bytes, 399696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 116 MiB, 121614336 bytes, 237528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 496 KiB, 507904 bytes, 992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop7: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0002d4c2


Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048   40962047   40960000  19.5G 83 Linux
/dev/sda2         40962048 1887989759 1847027712 880.7G 83 Linux
/dev/sda3       1887989760 1953523711   65533952  31.3G 82 Linux swap / Solaris








Disk /dev/loop8: 180.5 MiB, 189272064 bytes, 369672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop9: 834.7 MiB, 875270144 bytes, 1709512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop10: 834.7 MiB, 875208704 bytes, 1709392 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop11: 100.7 MiB, 105607168 bytes, 206264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop12: 221.6 MiB, 232333312 bytes, 453776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop13: 716 KiB, 733184 bytes, 1432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
tom@tom-HP-ProBook-450-G3:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G   18M  1.6G   2% /run
/dev/sda1        20G   17G  1.4G  93% /
tmpfs           7.8G   24M  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/loop2       87M   87M     0 100% /snap/core/5145
/dev/loop3      198M  198M     0 100% /snap/vlc/365
/dev/loop4      196M  196M     0 100% /snap/vlc/555
/dev/loop5      116M  116M     0 100% /snap/easy-disk-cleaner/4
/dev/loop6      512K  512K     0 100% /snap/ufw/14
/dev/loop8      181M  181M     0 100% /snap/vlc/190
/dev/loop7       87M   87M     0 100% /snap/core/4917
/dev/loop10     835M  835M     0 100% /snap/0ad/13
/dev/loop9      835M  835M     0 100% /snap/0ad/18
/dev/loop0       88M   88M     0 100% /snap/core/5328
/dev/loop1      908M  908M     0 100% /snap/0ad/30
/dev/loop11     101M  101M     0 100% /snap/easy-disk-cleaner/18
/dev/loop12     222M  222M     0 100% /snap/freecad/4
/dev/loop13     768K  768K     0 100% /snap/ufw/95
/dev/sda2       867G  485G  339G  59% /home
tmpfs           1.6G   12K  1.6G   1% /run/user/121
tmpfs           1.6G   32K  1.6G   1% /run/user/1000
tom@tom-HP-ProBook-450-G3:~$ 



```

---

### Post by deadflowr on 2018-09-16
The virtual machines are moot since they store in your home folder. (Normally, the default storage location for Virtulbox is in the Virtualbox Vms folder in the home folder.

What you do have are some fat /usr/ and /var folders.
The /var folder is actually a little easier to clean as it's where those pesky /snaps are actually located
(the snaps are basically images (like a disk or iso)  that get mounted at the /snap directory, but the images are actually located in the /var/lib/snapd/snaps folder)
But none of that is useful to what you need to do.
What you need to do is clear out the older snap revisions.
It's tedious, but should free some space.

Basically what you need to do is list all snaps
like so
```
snap list --all
```
this will output all snaps, including all versions (or aka revisions) of all snaps currently installed on the system.
now the tedious part

you would want to locate snaps which are listed as disabled and locate the revision number of those snaps.
Then to remove you need to run these commands
```
sudo snap remove <snap-name-here> --revision <number-here>
```
so for instance, as an example I see you have 0ad installed and have several revisions, so most likely you can remove the older ones.

Start with the oldest which is shown from the output as revision 13.
With the base command above to remove 0ad revision 13 it would be
```
sudo snap remove 0ad --revision 13
```
It'll scare you and say it's removing the 0ad snap, but it's only removing that single revision.

Run 
```
snap list --all
```
again will show that 0ad 13 is now gone.

From there you rinse and repeat the command structure against any other snaps listed as disabled.
When all done it should free a couple gigs.

The reason these are all installed is because snaps are automatically updated in the background.
But by design the system never removes older revision so if a new one fails somehow, you can revert to the older version if need be.
So the system fills up with junk after a while, especially with snaps that have routine updates.

Hope it helps.
Or makes sense.

---

### Post by HermanAB on 2018-09-17
Note that a VM can be saved anywhere.  I usually put them on a SD card or USB stick, in order to avoid clogging up my laptop HDD.

---

### Post by webmanoffesto on 2018-09-17
Thank you
What do you recommend for
core               16-2.33.1           4917  stable    canonical&#10003;  core,disabled

---

### Post by deadflowr on 2018-09-17
You can remove any revision of any snap if it's disabled and you don't think you'll ever have to revert back to it.
If all works as expected, then removing the older ones are fine.
You only need one core.

---

