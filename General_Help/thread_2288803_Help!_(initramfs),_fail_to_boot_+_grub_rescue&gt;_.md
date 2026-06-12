---
title: "Help! (initramfs), fail to boot + grub rescue&gt; + encrypted home"
date: 2015-07-30
forum: General Help
---

### Post by Victoria_C. on 2015-07-30
Hola, 

I'm new here, I have been using ubuntu for years, with out much issues, until now, and I'm panicking cause I cant fix it on my own. I have searched for help online, but I think I made it worse. I'm not sure what I can do to get back my OS and files...

I cant boot to my ubuntu 15.04, after boot I get to initramfs. I introduced the command blkid but I don't know what that is. I'm trying to find a solution and not loose my files, I don't know what to do. I tried the prefix thing but I cant get/find the right path for insmod linux command in /boot and grub/ in sda1.

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

(initramfs) blkid 
/dev/sda1: UUID="513ffff2-7be9-4ca7-8ccb-740fa815e0bc" TYPE="ext2"
/dev/sda5: UUID="732492df-7da7-4b39-a2df-dc7ecbe57134" TYPE="crypto_LUKS"
/dev/sdb1: LABEL="UUI" UUID="2CFF-8706" TYPE="vfat"


I have an ubuntu USB live, and had tried the boot-repair, but now I can't boot grub2 and instead I'm on grub rescue> I also encrypted home when I installed, but I cant mount it, I have tried the sudo fdisk -l command but not sure what I must do next when trying to mount the /dev/sda1 point cause I get a message saying there is no mount point... I can't mount /dev/sda1 for some reason, I'm sure I'm doing something wrong but can't see what...
[INDENT]ubuntu@ubuntu:~$ sudo fdisk -l
[/INDENT]Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000efb3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   488396799   243947521    5  Extended
/dev/sda5          501760   488396799   243947520   83  Linux

Disk /dev/sdb: 7803 MB, 7803174912 bytes
152 heads, 35 sectors/track, 2864 cylinders, total 15240576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a8e5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15239167     7618560    b  W95 FAT32

---

### Post by oldfred on 2015-07-30
I do not use LVM nor full drive encryption as it adds a lot of complications. But if you need encrytion you have to learn about LVM.

 Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

 fsck on encrypted LUKS 
[http://serverfault.com/questions/375090/using-fsck-to-check-and-repair-luks-encrypted-disk](http://serverfault.com/questions/375090/using-fsck-to-check-and-repair-luks-encrypted-disk)

---

### Post by Victoria_C. on 2015-07-30
Thanks for the reply, Ill definitely need to read carefully all those links, there is a lot to read there. I'm not sure about why would I need to learn about LVM, I have my password and that should be enough... I don't want to brute force the decryption.

Do you think I'm having issues with the mounting of sda1 because its encrypted with sda5?

---

### Post by oldfred on 2015-07-30
Did you have an abnormal shutdown  or force system to shutdown?

That can cause file corruption that needs fsck or sometimes corruption just happens.
I think you first need to mount LVM partition and give passphrase to open encrypted partition. Then you can run fsck and see if that repairs it.

---

### Post by Victoria_C. on 2015-07-31
Thanks for the reply, Ill definitely need to read carefully all those links, there is a lot to read there. I'm not sure about why would I need to learn about LVM, I have my password and that should be enough... I don't want to brute force the decryption.

Do you think I'm having issues with the mounting of sda1 because its encrypted with sda5?

---

### Post by oldfred on 2015-07-31
Most system repairs need not just the /boot partition mounted but at least parts of the rest of the install. Those parts are then inside the LVM, so you have to mount it also.

If you just need fsck on your boot partition:

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

But to run fsck on your encrypted partition you need to mount it.

---

### Post by Victoria_C. on 2015-08-11
Hola, 

Im still trying to fix this :( 

After booting from Live USB, I'm not sure if I mounted or not... Im not sure what Im doing there. I notice on Hom that 2 devices appear, 1 is encrypted but when I click to mount it I get an error.

[http://i.imgur.com/T1K7TKy.png](http://i.imgur.com/T1K7TKy.png)

If I open terminal and use fdisk -l I still get this. 

[IMG]http://i.imgur.com/4piJvGe.png[/IMG]

How do I know if I unmounted or mounted the necessary partitions? How do I know which are needed beside /boot (which I assume is in sda1)? 

You mentioned those parts are inside LVM? I don't know if I have LVM, if I have it and its needed how do I mount it?

I have tried to run fsck but nothing happened... How do I mount the encrypted partition (which I guessing is sda5).

I'm scared to run > sudo e2fsck -C0 -p -f -v /dev/sda1 without knowing how to mount the right partition and encrypted partition.

Is fsck the same as e2fsck? 
 
I used another Hard Drive to install a temporary OS (Lubuntu and without encrypting Home), and somehow when I was transferring files there I managed to crash it. I booted again and to my horror I saw another initramfs. Since this was a temp one (and I wasn't afraid to delete my files in the process) I went to look for more solutions and found this one that WORKED for that one right away.

[http://bernaerts.dyndns.org/linux/74-ubuntu/232-ubuntu-boot-failure-initramfs](http://bernaerts.dyndns.org/linux/74-ubuntu/232-ubuntu-boot-failure-initramfs)


I was about to try the same with my original HD and OS, but nticed that after the prompt I got a very different filesystem. 

> [FONT=verdana][SIZE=2]Disk /dev/sdb: 7803 MB, 7803174915 bytes
[/SIZE][/FONT]
[FONT=verdana][SIZE=2]64 heads, 32 sectors/track, 7441 cylinders, total 15240576 sectors
[/SIZE][/FONT]
[FONT=verdana][SIZE=2]Units = sectors of 1 * 512 = 512 bytes
[/SIZE][/FONT]
[FONT=verdana][SIZE=2]Sector size (logical/physical): 512 bytes / 512 bytes
[/SIZE][/FONT]
[FONT=verdana][SIZE=2]I/O size (minimum/optimal): 512 bytes / 512 bytes
[/SIZE][/FONT]
[FONT=verdana][SIZE=2]Disk identifier: 0x5f55bd3d

[/SIZE][/FONT]
[FONT=verdana][SIZE=2]     Device      Boot           Start                         End               Blocks         Id      System
[/SIZE][/FONT]
[FONT=verdana][SIZE=2]/dev/sdb1           *                64                 1529855               764896        17     Hidden HPFS/NTFS

[/SIZE][/FONT]
[FONT=verdana][SIZE=2]Disk /dev/mapper/sda5_crypt: 249.8 GB 249800163328 bytes
[/SIZE][/FONT]
[FONT=verdana][SIZE=2]255 heads, 63 sectors/track, .0369 cylinders, total 487890944 sectors
[/SIZE][/FONT]
[FONT=verdana][SIZE=2]Units = sectors of 1 * 512 = 512 bytes
[/SIZE][/FONT]
[FONT=verdana][SIZE=2]Sectors size (logical/physical): 512 bytes / 512 bytes
[/SIZE][/FONT]
[FONT=verdana][SIZE=2]I/O size (minimum/optimal): 512 bytes / 512 bytes
[/SIZE][/FONT]
[FONT=verdana][SIZE=2]Disk Identifier: 0x00000000

[/SIZE][/FONT]
[FONT=verdana][SIZE=2]Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

[/SIZE][/FONT]
[FONT=verdana][SIZE=2]Disk /dev/mapper/ubuntu--vg-root: 247.7 GB, 247656873984 bytes
[/SIZE][/FONT]
[FONT=verdana][SIZE=2]255 heads, 63 sectors/track, 30109 cylinders, total 483704832 sectors
[/SIZE][FONT=verdana][SIZE=2]Units = sectors of 1 * 512 = 512 bytes
Sectors size (logical/physical): 512 bytes / 512 bytes
[/SIZE][/FONT]
[FONT=verdana][SIZE=2]I/O size (minimum/optimal): 512 bytes / 512 bytes
[/SIZE][/FONT]
[SIZE=2]Disk Identifier: 0x00000000

[/SIZE][/FONT]
[FONT=verdana][SIZE=2]Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

[/SIZE][/FONT]
[FONT=verdana][SIZE=2]Disk /dev/mapper/ubuntu--vg-swap_1: 2139 MB, 2139095040 bytes
[/SIZE][/FONT]
[FONT=verdana][SIZE=2]255 heads, 63 sectors/track, 260 cylinders, total 4177920 sectors
[/SIZE][FONT=verdana][SIZE=2]Units = sectors of 1 * 512 = 512 bytes
Sectors size (logical/physical): 512 bytes / 512 bytes
[/SIZE][/FONT]
[FONT=verdana][SIZE=2]I/O size (minimum/optimal): 512 bytes / 512 bytes
[/SIZE][/FONT]
[SIZE=2]Disk Identifier: 0x00000000

[/SIZE][/FONT]
[SIZE=2]Disk /dev/mapper/ubuntu-vg-swap_1 doesn't contain a valid partition table[/SIZE]

And then I doubted about the command listed in that website, so  I came again to ask for directions if I'm doing something right or I'm risking o brick my hard drive?

I remember it asked me my password right before prompt, so I'm guessing I mounted the encrypted partition. But the file system is different there... and different from the Lubuntu that worked (if I'm not mistaken it was an EXT3).

Would fsck.ext3 -f /dev/sda1 work on my original problem? Or do i apply the e2fsck command that you told me about?

---

### Post by oldfred on 2015-08-11
With terminal output please just copy & paste into response, not a screen shot. If gui screen use forums advanced editor and paperclip icon to attach screen shots, not post in line. Not everyone has high speed Internet.

I know fsck & e2fsck are doing the same thing, not sure if now exactly same or not. If you want to know about a command.
man fsck
man e2fsck

Your boot partition is not inside the LVM and is sda1, so you can run fsck directly on it.
But since sda5 is just a container for the LVM,  you have to mount the LVM. You may not have the driver for LVM and may need to install this:
sudo apt-get install lvm2

It should not show info on [FONT=verdana][SIZE=2]/dev/mapper/ubuntu--vg-root as it is encrypted.
But when you mount it, it should ask for pass phrase.
I think this thread discusses more about LVM & encryption. It is more on resizing but shows all the details with some explanation you need for mounting. If you use another install to mount, it is then just like this example is using live installer.
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

General LVM info
      [/SIZE][/FONT] Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

    [FONT=verdana][SIZE=2]
[/SIZE][/FONT]

---

### Post by Victoria_C. on 2015-08-11
Here is what I did, Im about to reboot. I didnt saw any error after the e2fsck.

>  sudo apt-get install lvm2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lvm2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

> df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            991M     0  991M   0% /dev
tmpfs           201M  9.1M  192M   5% /run
/dev/sdb        1.1G  1.1G     0 100% /cdrom
/dev/loop0      1.1G  1.1G     0 100% /rofs
/cow           1003M  112M  892M  12% /
tmpfs          1003M  276K 1003M   1% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs          1003M     0 1003M   0% /sys/fs/cgroup
tmpfs          1003M  8.0K 1003M   1% /tmp
tmpfs           201M   32K  201M   1% /run/user/999


> sudo blkid
/dev/sda1: UUID="513ffff2-7be9-4ca7-8ccb-740fa815e0bc" TYPE="ext2" PARTUUID="000efb3e-01"
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="732492df-7da7-4b39-a2df-dc7ecbe57134" TYPE="crypto_LUKS" PARTUUID="000efb3e-05"
/dev/sdb1: UUID="2015-04-22-13-12-39-00" LABEL="Ubuntu-MATE 15.04 i386" TYPE="iso9660" PARTUUID="04ecbde7-01"

> sudo cryptsetup status crypt1
/dev/mapper/crypt1 is inactive.

> ubuntu-mate@ubuntu-mate:~$ sudo lvdisplay
  No volume groups found

> ubuntu-mate@ubuntu-mate:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,relatime,size=1014752k,nr_inodes=214076,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=205268k,mode=755)
/dev/sdb on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec   				
 		
 		 	
 
   	 		
 		 		 	
  	 		 			 			 			

 			 			 		

,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=23,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=205268k,mode=700,uid=999,gid=999)

> ubuntu-mate@ubuntu-mate:~$ sudo modprobe dm-crypt
> 
ubuntu-mate@ubuntu-mate:~$ sudo cryptsetup luksOpen /dev/sda5 crypt1
Enter passphrase for /dev/sda5: 

> ubuntu-mate@ubuntu-mate:~$ sudo vgscan --mknodes
  Reading all physical volumes.  This may take a while...
  Found volume group "ubuntu-vg" using metadata type lvm2
> 
ubuntu-mate@ubuntu-mate:~$ sudo vgchange -ay
  2 logical volume(s) in volume group "ubuntu-vg" now active

> ubuntu-mate@ubuntu-mate:~$  sudo e2fsck -C0 -p -f -v /dev/sda1
                                                                               
         596 inodes used (0.96%, out of 62248)
          98 non-contiguous files (16.4%)
           2 non-contiguous directories (0.3%)
             # of inodes with ind/dind/tind blocks: 98/15/0
      145431 blocks used (58.45%, out of 248832)
           0 bad blocks
           0 large files

         576 regular files
          11 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
         587 files




---

### Post by Victoria_C. on 2015-08-11
Oh boy... I rebooted hoping that it was fixed, but I got to the same:

[ 1.311068] ACPI PCC probe failed.
starting version 219
mount: mounting /dev/mapper/ubuntu--vg-root on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.22.1 (Ubuntu 1:1.22.0-9ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

---

### Post by oldfred on 2015-08-11
I see you ran the fsck on the sda1, but you may need to run it  on the /mapper after it is mounted and unencrypted.

---

### Post by Victoria_C. on 2015-08-11
I&#8217;m sorry, I&#8217;m not sure how to mount the mapper, I have been looking for online resources on that like this one, but I&#8217;m not sure if its what I&#8217;m looking for. 

>  The exact method depends on how you have setup luks, and if you have  LVM on top of luks or if you just have a filesystem within the luks  volume.

  If you don't have LVM in addition to luks then you would probably do something like this.
  cryptsetup luksOpen /dev/rawdevice somename
fsck /dev/mapper/somename

# or

cryptsetup luksOpen /dev/sda2 _dev_sda2
fsck /dev/mapper/_dev_sda2
  If you used the LVM on LUKS option providied by the Debian/Ubuntu installer, then you'll need to start up LVM.  So vgchange -aly after opening the encrypted volume, then run fsck against the /dev/mapper/lvname.

     


> For whatever reason cryptsetup luksOpen /dev/rawdevice somename wasn't working out to give me something to run fsck on, although it was showing up with vgscan just fine after vgchange -ay as 'active'... I had to create the raw devices manually with vgscan --mknodes and then fsck on the logical volume showing up in vgscan with fsck /dev/cryptVG/root - Hope this helps someone else out there

---

### Post by oldfred on 2015-08-11
I know some like LVM, and others need encryption, but I do not use either as they seem too complex. I want reliability and ease of use. Something I can easily understand enough details to repair and use.

I think you posted your mapper as [FONT=verdana][SIZE=2]/dev/mapper/ubuntu--vg-root?[/SIZE][/FONT]

---

### Post by Victoria_C. on 2015-08-12
You are right, I would also prefer ease or use and reliability, more so when broke out. Im planning to do a fresh OS install once I get my files (hopefully) and will keep it simple without LVM or Home encryption. I have seen many posts about that home encryption issues lately.

Ohh I think this is it right? 

[FONT=verdana][SIZE=2]/dev/mapper/sda5_crypt 

or is it?

[FONT=verdana][SIZE=2]/dev/mapper/ubuntu--vg-root

[/SIZE][/FONT]Both are /mapper? Which one is it? [/SIZE][/FONT]How do I mount it? Then I will need to use this command? 

fsck /dev/mapper/sda5_crypt
 
or 

fsck /dev/mapper/ubuntu--vg-root

or is it:

cryptsetup luksOpen /dev/sda1

Which I think will ask me my password. Then:

fsck /dev/mapper/ubuntu--vg-root

 To tell you the truth I dont even know if I have LVM

[https://i.imgur.com/mwQ3d.jpg](https://i.imgur.com/mwQ3d.jpg)

---

### Post by oldfred on 2015-08-12
I do not not know details of internal of LVM.
You do have LVM as the /dev/mapper shows & all installs with full drive encryption use LVM.

Your sda1 is your /boot partition and is not encrypted, so this cannot be correct.
cryptsetup luksOpen /dev/sda1

But I think you mount the lvm or [FONT=verdana][SIZE=2][FONT=verdana][SIZE=2]/dev/mapper/ubuntu--vg-root.
But I do not know how encrypted is shown inside the LVM.

I thought this post showed all the detail commands you need to run in order. And just before he starts on the resizing he mentions you can also do maintenance like fsck.
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by Victoria_C. on 2015-08-12
Ok, I think I got this to work:

> sudo e2fsck -f /dev/mapper/ubuntu--vg-root

Cause I got a huge continuous list of this, followed by a huge ammount of numbers filling the whole screen. 

> Free inodes count wrong (15122421, counted=14505550).
Fix<y>? yes

And no I can see what you meant with this since I had to press manually y:

> #if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

When it stopped i got this message:
> 
/dev/mapper/ubuntu--vg-root: ***** FILE SYSTEM WAS MODIFIED *****
/dev/mapper/ubuntu--vubuntu-mate@ubuntu-mate:~$ sudo e2fsck -f /dev/mapper/ubuntu--vg-root
e2fsck 1.42.12 (29-Aug-2014)
/dev/mapper/ubuntu--vg-root is mounted.
g-root: 616882/15122432 files (2.1% non-contiguous), 50369175/60463104 blocks

I tried to follow the instuctions on the LVM resizing guide that you linked, and I cheked that the file system is intact with e2fsck again:
> 
ubuntu-mate@ubuntu-mate:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.42.12 (29-Aug-2014)
/dev/sda1 is mounted.
e2fsck: Cannot continue, aborting.

ubuntu-mate@ubuntu-mate:~$ sudo e2fsck -f /dev/mapper/ubuntu--vg-root
e2fsck 1.42.12 (29-Aug-2014)
/dev/mapper/ubuntu--vg-root is mounted.

I displayed the LVM with lvdisplay and got this:

> ubuntu-mate@ubuntu-mate:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                ocMdNU-Ozqn-U8gZ-ejP4-14lA-MxLn-HQDF4L
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-11-17 04:17:28 +0000
  LV Status              available
  # open                 1
  LV Size                230.65 GiB
  Current LE             59046
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                6b1AWV-p0dq-LKPc-aCcM-QijN-hQVV-Ansm06
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-11-17 04:17:29 +0000
  LV Status              available
  # open                 0
  LV Size                1.99 GiB
  Current LE             510
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
   
And for the first time since this happened, I could see the contents of my original file system, still I cant access to home folder cause I get a warning window with this, but I think its a good sign:

> 
The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "*my file system*".

Im about to reboot and find out what is next.

---

### Post by oldfred on 2015-08-12
Sounds like progress.
I think now you know more about LVM & encryption than I do.

With encryption really good regular backups are vital. As once system has corruption, you often cannot recover it and have to revert to backup to restore a new system.

---

