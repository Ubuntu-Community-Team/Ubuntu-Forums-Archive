---
title: "grub-install fails on cloned hd to ssd"
date: 2020-06-09
forum: General Help
---

### Post by mue.de on 2020-06-09
Hi community,

i tried to clone an old hdd (60GB) with two partitions ('/' at sda1, '/home' at sda5) to a new ssd (120GB).
On the old hdd i was running Ubuntu 18.04, 64-bit; for the cloning i used an Ubuntu 16.04 (amd64) Bootstick.
The two partitions are now on 'sda1' ('/') and 'sda2' ('/home') with the contents from the old hd.
So i tried to install grub after chroot into the new system, here the commands and results:

The parameters of the old hd:
```

sudo fdisk -l
Festplatte /dev/sda: 55,9 GiB, 60011642880 Bytes, 117210240 Sektoren
Einheiten: Sektoren von 1 * 512 = 512 Bytes
Sektorgröße (logisch/physikalisch): 512 Bytes / 512 Bytes
E/A-Größe (minimal/optimal): 512 Bytes / 512 Bytes
Festplattenbezeichnungstyp: dos
Festplattenbezeichner: 0x7b602b0c

Gerät      Boot    Anfang      Ende Sektoren Größe Kn Typ
/dev/sda1  *         2048  41078783 41076736 19,6G 83 Linux
/dev/sda2        41078784 117209087 76130304 36,3G  5 Erweiterte
/dev/sda5        41080832 109203455 68122624 32,5G 83 Linux
/dev/sda6       109205504 117209087  8003584  3,8G 82 Linux Swap / Solaris

GNU Parted 3.2
/dev/sda wird verwendet
Willkommen zu GNU Parted! Rufen Sie »help« auf, um eine Liste der verfügbaren Befehle zu
erhalten.
(parted) p
Modell: ATA HITACHI HTS54166 (scsi)
Festplatte  /dev/sda:  60,0GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos
Disk-Flags: 

Nummer  Anfang  Ende    Größe   Typ       Dateisystem     Flags
 1      1049kB  21,0GB  21,0GB  primary   ext4            boot
 2      21,0GB  60,0GB  39,0GB  extended
 5      21,0GB  55,9GB  34,9GB  logical   ext4
 6      55,9GB  60,0GB  4098MB  logical   linux-swap(v1)

```

Here the paramters of the new ssd with the cloned partitions 'sda1' ('/) and 'sda2' ('/home', formerly on 'sda5')

```

kubuntu@kubuntu:~$ blkid
/dev/sda1: LABEL="/" UUID="f40dead2-a54d-4880-b5e3-7b88b3b5681b" TYPE="ext4" PARTUUID="06bef2ee-2375-4847-9d1b-58de46222831"
/dev/sda2: LABEL="/home" UUID="be6de963-77d5-4adf-b888-b4f0bb06a40e" TYPE="ext4" PARTUUID="8993b1e7-68e5-45ca-a86f-8e60cac797b8"


kubuntu@kubuntu:~$ lsblk -f -o +SIZE,MODEL
NAME   FSTYPE   LABEL                     UUID                                 MOUNTPOINT   SIZE MODEL
loop0  squashfs                                                                /rofs        1,7G 
sda                                                                                       111,8G Intenso SSD Sata
&#9500;&#9472;sda1 ext4     /                         f40dead2-a54d-4880-b5e3-7b88b3b5681b             46,9G 
&#9500;&#9472;sda2 ext4     /home                     be6de963-77d5-4adf-b888-b4f0bb06a40e             56,7G 
&#9492;&#9472;sda3 swap     swap                      1de986fc-8f77-47a7-96d7-6d3e3e24e8d4 [SWAP]         8G 
sdb    iso9660  Kubuntu 18.04.2 LTS amd64 2019-02-10-00-41-52-00               /cdrom       7,5G Cruzer          
&#9500;&#9472;sdb1 iso9660  Kubuntu 18.04.2 LTS amd64 2019-02-10-00-41-52-00                            1,8G 
&#9492;&#9472;sdb2 vfat     Kubuntu 18.04.2 LTS amd64 5655-3E5A                                         2,4M 
sr0                                                                                        1024M DVD/CDRW UJDA775

```

The live-system:
```

kubuntu@kubuntu:~$ mount |grep /dev/sd
/dev/sdb on /cdrom type iso9660 (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)
/dev/sdc1 on /media/kubuntu/Transcend type vfat (rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)
kubuntu@kubuntu:~$ 

```

Mounting the new partitions:
```

kubuntu@kubuntu:/mnt$ sudo mkdir _
kubuntu@kubuntu:/mnt$ sudo mkdir _/home
kubuntu@kubuntu:/mnt$ sudo mount /dev/sda1 _
kubuntu@kubuntu:/mnt$ sudo mount /dev/sda2 _/home

kubuntu@kubuntu:/mnt$ mount |grep /dev/sd
/dev/sdb on /cdrom type iso9660 (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)
/dev/sdc1 on /media/kubuntu/Transcend type vfat (rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)
/dev/sda1 on /mnt/_ type ext4 (rw,relatime)
/dev/sda2 on /mnt/_/home type ext4 (rw,relatime)

```

'chroot' to the new sytem:

```
kubuntu@kubuntu:/mnt$ for dir in /dev /dev/pts /proc /sys /run; do sudo mount --bind $dir /mnt/_$dir; done

kubuntu@kubuntu:/mnt$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=977136k,nr_inodes=244284,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=199920k,mode=755)
/dev/sdb on /cdrom type iso9660 (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=26,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=14638)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=199920k,mode=700,uid=999,gid=999)
/dev/sdc1 on /media/kubuntu/Transcend type vfat (rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)
/dev/sda1 on /mnt/_ type ext4 (rw,relatime)
/dev/sda2 on /mnt/_/home type ext4 (rw,relatime)
udev on /mnt/_/dev type devtmpfs (rw,nosuid,relatime,size=977136k,nr_inodes=244284,mode=755)
devpts on /mnt/_/dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
proc on /mnt/_/proc type proc (rw,nosuid,nodev,noexec,relatime)
sysfs on /mnt/_/sys type sysfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /mnt/_/run type tmpfs (rw,nosuid,noexec,relatime,size=199920k,mode=755)


kubuntu@kubuntu:/mnt$ sudo chroot _
root@kubuntu:/# mount

/dev/sda1 on / type ext4 (rw,relatime)
/dev/sda2 on /home type ext4 (rw,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=977136k,nr_inodes=244284,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=199920k,mode=755)
root@kubuntu:/# 


```

trying to install 'grub' on /dev/sda
```

root@kubuntu:/# grub-install /dev/sda
i386-pc wird für Ihre Plattform installiert.
grub-install: Warnung: Diese GPT-Partitionsbezeichnung hat keine BIOS-Boot-Partition, Einbettung würde unmöglich sein.
grub-install: Warnung: Einbettung ist nicht möglich. GRUB kann in dieser Konfiguration nur mittels Blocklisten installiert werden. Blocklisten sind allerdings UNZUVERLÄSSIG und deren Verwendung wird daher nicht empfohlen..
grub-install: Fehler: mit Blocklisten wird nicht fortgesetzt.
root@kubuntu:/# 

root@kubuntu:/# cat /etc/fstab                                            
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f40dead2-a54d-4880-b5e3-7b88b3b5681b       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=be6de963-77d5-4adf-b888-b4f0bb06a40e       /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=1de986fc-8f77-47a7-96d7-6d3e3e24e8d4       none            swap    sw              0       0
root@kubuntu:/# 

root@kubuntu:/# for dir in /run /sys /proc /dev; do sudo umount $dir; done
umount: /dev: das Ziel wird gerade benutzt.

```


I've also a copy of the mbr of the old hdd (1st Block of 1KB of /dev/sda); is it recommended writing it back to the new ssd?

Thanks for any advice

---

### Post by oldfred on 2020-06-09
Google translate says the error is from grub trying to install to a gpt partitioned drive and you do not have the bios_grub partition.
And if gpt you have to have a 1 or 2MB unformated partition with the bios_grub flag if using gparted to create it.

But your fdisk and parted listing show drive is MBR(msdos). And there is no extended partition with gpt.
Was drive gpt before? 

Windows tools incorrectly convert a gpt drive to MBR, leaving backup gpt partition table. But then Linux tools see both MBR and gpt and get confused.

I prefer gpt, and it is only required if you want to boot Windows in BIOS mode.
You can use gpt with Ubuntu in either BIOS or UEFI boot mode, but need supporting partitions. A bios_grub for BIOS boot or an ESP - efi system partition for UEFI boot. When I was planning on converting from BIOS to UEFI I used both on same drive without issue, but that was only because system was BIOS, but I expected to move drive to a new UEFI system.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

You may need to either clear old gpt data or convert to gpt and add the tiny bios_grub partition.

FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by mue.de on 2020-06-10
Hello oldfred,

thanks for your immediate reply.
I think, i was to uninformed about 'gpt', when i tried to clone the hdd.

The old hdd (on the *Lenovo T61) *had no gpt, only a master boot record (mbr), no UEFI-boot.

On that Laptop i don't use Windows; i prepared it for my wife years ago (i bought it used in 2012) only with[I] Ubuntu.
[/I]Now, in times of *Corona* it was a bit slow in Video-Conferences; therefore the 'upgrade' to the ssd.


So i would like to use the gpt-method.
But following the [post]9144643[/post], the link to [http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition) is broken.

I don't like tools in that state, when i'm booting a live system, so i can create a bios boot partition in the 128MB free, unallocated space i left at  the beginning of the ssd?
Can i do this by using *parted*?

The Backups (as image-files) are still safe on the external 4TB hdd

So i will try your advice (and donate a bit):
> Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)


---

### Post by oldfred on 2020-06-10
I have always use gparted on Ubuntu live installer to create partitions.
You can use any partitioning tool to create an unformatted 1 or 2MB partition anywhere inside the first 2TB of a drive for bios_grub.
[https://www.gnu.org/software/parted/manual/html_node/set.html](https://www.gnu.org/software/parted/manual/html_node/set.html)

If starting over you can convert drive and use cp with -a or rsync with several parameters to copy data from MBR to gpt. You cannot image copy partitions from MBR to gpt.

Some technical info on gpt:
[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)

I have only used gparted and occasionally gdisk which is also now on Ubuntu live installer.
[https://bbs.archlinux.org/viewtopic.php?id=168580](https://bbs.archlinux.org/viewtopic.php?id=168580)

If you convert to gpt, you will have to totally reinstall grub.
Many find Boot-Repair easier to reinstall grub.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

If using gpt with BIOS create a 1MB bios_grub partition with no format. 
 Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... Or if drive is blank or you want to erase it. If drive is not blank this will erase it, so have good backups.
sudo parted /dev/sda mklabel gpt
Create a mebibyte partition (+1M with fdisk or gdisk) on the disk with no file system and with partition type BIOS boot. Select BIOS boot and partition type number 4 for fdisk, ef02 for gdisk, and bios_grub for parted. This partition can be in any position order but has to be on the first 2 TB of the disk.

Older gparted screen shots, but still the same, just updated graphics. Create gpt drive, and right click on a partition to set bios_grub.

---

### Post by mue.de on 2020-06-11
Hello oldfred,

your help was crucially for me, the system is now running perfectly with all the programs installed.
I havn't seen the flag 'Bios_GPT'  in parted, since only the entry 'Apple TV' was visible, so i tried to make an extra 'boot'-Partition on the free space (128MB) of the ssd, named it '/boot', put an entry (UUID-form) in the '/etc/fstab'.
-> The system only booted in 'emergency mode'.
Then, following your advice i removed this entry in the 'fstab', cleared the 'boot'-partition and changed it's flag to 'Bios_GPT'.
So, as the result, the old Lenovo T61 with 2GB RAM and the 120GB ssd is now much quicker than before running an actual [I]Ubuntu Bionic Beaver (18.04.4 LTS).

[/I]If it's usefull for others i could recapitulate the steps (in short) i went moving an entire Ubuntu-System from a small hdd (60GB) to a new ssd (120GB), which cost less than 50$.
```

root@kubuntu:/# lsblk -f -o +SIZE,MODEL
NAME   FSTYPE   LABEL                     UUID                                 MOUNTPOINT   SIZE MODEL
loop0  squashfs                                                                             1,7G 
sda                                                                                       111,8G Intenso SSD Sata
&#9500;&#9472;sda1 ext4     /                         f40dead2-a54d-4880-b5e3-7b88b3b5681b /           46,9G 
&#9500;&#9472;sda2 ext4     /home                     be6de963-77d5-4adf-b888-b4f0bb06a40e /home       56,7G 
&#9500;&#9472;sda3 swap     swap                      1de986fc-8f77-47a7-96d7-6d3e3e24e8d4 [SWAP]         8G 
&#9492;&#9472;sda4 ext4     /boot                     0d299b13-54f2-4ae5-a465-d30d434c673d              128M 
sdb    iso9660  Kubuntu 18.04.2 LTS amd64 2019-02-10-00-41-52-00                            7,5G Cruzer          
&#9500;&#9472;sdb1 iso9660  Kubuntu 18.04.2 LTS amd64 2019-02-10-00-41-52-00                            1,8G 
&#9492;&#9472;sdb2 vfat     Kubuntu 18.04.2 LTS amd64 5655-3E5A                                         2,4M 
sdc                                                                                          15G Transcend 16GB  
&#9492;&#9472;sdc1 vfat     Transcend                 504D-FDB2                                          15G 
sr0                                                                                        1024M DVD/CDRW UJDA775
root@kubuntu:/# 


### Neuer Tipp von oldfred: die Boot-Partition da&#341;f nicht formatiert sein, sie muß das Flag 'GPT_Bios' erhalten: gemacht; läuft !!!
### Super!
root@kubuntu:/# lsblk -f -o +SIZE,MODEL
NAME   FSTYPE   LABEL                     UUID                                 MOUNTPOINT   SIZE MODEL
loop0  squashfs                                                                             1,7G 
sda                                                                                       111,8G Intenso SSD Sata
&#9500;&#9472;sda1 ext4     /                         f40dead2-a54d-4880-b5e3-7b88b3b5681b /           46,9G 
&#9500;&#9472;sda2 ext4     /home                     be6de963-77d5-4adf-b888-b4f0bb06a40e /home       56,7G 
&#9500;&#9472;sda3 swap     swap                      1de986fc-8f77-47a7-96d7-6d3e3e24e8d4 [SWAP]         8G 
&#9492;&#9472;sda4 ext4     /boot                     0d299b13-54f2-4ae5-a465-d30d434c673d              128M 
sdb    iso9660  Kubuntu 18.04.2 LTS amd64 2019-02-10-00-41-52-00                            7,5G Cruzer          
&#9500;&#9472;sdb1 iso9660  Kubuntu 18.04.2 LTS amd64 2019-02-10-00-41-52-00                            1,8G 
&#9492;&#9472;sdb2 vfat     Kubuntu 18.04.2 LTS amd64 5655-3E5A                                         2,4M 
sdc                                                                                          15G Transcend 16GB  
&#9492;&#9472;sdc1 vfat     Transcend                 504D-FDB2                                          15G 
sr0                                                                                        1024M DVD/CDRW 

root@kubuntu:/# nano /etc/fstab
root@kubuntu:/# mount
/dev/sda1 on / type ext4 (rw,relatime)
/dev/sda2 on /home type ext4 (rw,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=977136k,nr_inodes=244284,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=199920k,mode=755)


root@kubuntu:/# grub-install /dev/sda
i386-pc wird für Ihre Plattform installiert.
Installation beendet. Keine Fehler aufgetreten.
root@kubuntu:/# 

root@kubuntu:/# fdisk -l /dev/sda
Festplatte /dev/sda: 111,8 GiB, 120034123776 Bytes, 234441648 Sektoren
Einheiten: Sektoren von 1 * 512 = 512 Bytes
Sektorgröße (logisch/physikalisch): 512 Bytes / 512 Bytes
E/A-Größe (minimal/optimal): 512 Bytes / 512 Bytes
Festplattenbezeichnungstyp: gpt
Festplattenbezeichner: EBB088EB-61CB-4534-BD5D-FF27BD527508

Gerät         Anfang      Ende  Sektoren Größe Typ
/dev/sda1     264192  98568191  98304000 46,9G Linux-Dateisystem
/dev/sda2   98568192 217382911 118814720 56,7G Linux-Dateisystem
/dev/sda3  217382912 234160127  16777216    8G Linux Swap
/dev/sda4       2048    264191    262144  128M BIOS boot

Partitionstabelleneinträge sind nicht in Festplatten-Reihenfolge.
root@kubuntu:/# 

```

Thanks a lot for your help!

Ewald

---

### Post by oldfred on 2020-06-11
Desktop installs now do not typically use a /boot partition, but a few very old systems had a BIOS that needed either a /boot or all of / (root) inside the first 130GB of a drive. Even then just have a 25 or 30GB / at beginning of drive & use rest as /home or data.

My 2006 laptop with only 1.5GB of RAM and slow HDD would not install full Ubuntu 20.04. My last working install on it was 12.04, but I installed 16.04 just to see if it would work & it did. Full install of 12.04 was so slow as to be unworkable. And 16.04 was functional but slow. I typically then installed fallback or gnome-panel which is like Ubuntu was before or old gnome2 and is a lighter weight gui.

With 20.04, I had to install server, then gnome-panel. But that did not install all the dependencies and had install more of gnome. But it now works with 20.04. 
[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)
[https://wiki.gnome.org/Projects/GnomePanel](https://wiki.gnome.org/Projects/GnomePanel)
May have to see if my old first SSD of 60GB would work in the old laptop.

---

