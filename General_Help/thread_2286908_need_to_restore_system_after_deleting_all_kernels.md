---
title: "need to restore system after deleting all kernels"
date: 2015-07-15
forum: General Help
---

### Post by jim97 on 2015-07-15
I deleted all of the kernels from my /boot directory and now the system can't boot.

Computer:  old i386 w/30 gib hard drive and 1543332 kb mem.  32 bit

Trying to follow the instructions here [http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)  but my system has the following.

> 
Model: ATA WDC WD300BB-00AU (scsi)
Disk /dev/sda: 30.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   30.0GB  29.8GB  extended
 5      257MB   30.0GB  29.8GB  logical                lvm

Model:  Memorex TD 2B (scsi)
Disk /dev/sdf: 1028MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  1028MB  1028MB  primary  fat16        boot

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 1611MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  1611MB  1611MB  linux-swap(v1)

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 28.1GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  28.1GB  28.1GB  ext4

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
                                                                            Error: Can't have a partition outside the disk!


But when I do:   sudo mount /dev/sda1 /mnt 
then:  sudo mount --bind /dev  /mnt/dev
I get an error:  mount point /mnt/dev does not exist.

Running ls /mnt  gets  grub  lost+found  memtest86+.bin   memtest86+.elf    


All the other directions involving creating a /mnt/  subdirectory also fail.

Is there a way I can find which kernel to reinstall and then the download it to a memstick and copy it into the broken system?
The system was up to date before my deleting everything.

Thanks
Jim

---

### Post by sudodus on 2015-07-15
Try to create the directory before trying to mount onto it:

```
sudo mkdir /mnt/dev
```

1. It is worth trying for a while, but if no luck, it is better to

2. Backup all your personal data

3. Reinstall Ubuntu - if you select Something else at the partitioning window, and do ***not*** format the root partition, at least some of your tweaks etc might survive.

4. If this does not work, make a clean installation. It is often faster than to try hard to repair a damaged system.

---

### Post by jim97 on 2015-07-15
sudodus

  Ive been trying that idea for the /dev /proc and /sys directories but when I try to chroot it says it can't find /bin/bash

Just to make it more fun the DVD unit died and I have another hooked up now so I will try some more.

Thanks
Jim

---

### Post by sudodus on 2015-07-15
Maybe this link will give you some tips to get further

[https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot)

You can also browse the internet for tutorials about using chroot.

---

### Post by jim97 on 2015-07-15
Well I've tried several posts.   Chroot seems to have problems because the file system is in a LVM and only /boot is can be seen.  Plus the /boot directory is very small (256MB) and I can't use the command 'ldd /bin /lib  /mnt/temp'  to overcome that.   

Repair thru grub isn't there,  when you select options it just reboots the computer.   LiveCD and repair doesn't work because the old installation isn't visible.  

Is there any way to fix this mess?   or is start from scratch by reinstalling?


Thanks
Jim

---

### Post by oldfred on 2015-07-15
You need to add the lvm2 driver and use the paths into your LVM.

I do not know LVM, but Boot-Repair knows it better and the total uninstall & reinstall of grub2 option I believe also adds the most current kernel. Or you can also add that.

---

### Post by sudodus on 2015-07-16
> **jim97 said:**
> Well I've tried several posts.   Chroot seems to have problems because the file system is in a LVM and only /boot is can be seen  ...  Is there any way to fix this mess?   or is start from scratch by reinstalling?

Thanks
Jim

I think that with LVM you should backup your personal files (documents, pictures, video clips, ...), and after that start from scratch by reinstalling.

---

### Post by steeldriver on 2015-07-16
You should be able to chroot with an LVM-based system - this is from memory so ymmv

```

vgchange -ay /dev/mapper/ubuntu--vg-root

mount /dev/mapper/ubuntu--vg-root /mnt

mount /dev/sda1 /mnt/boot

```

after which the rest of the process (bind mounts and so on) should be identical

---

### Post by jim97 on 2015-07-16
OldFred

Booted to LiveCD, into terminal, ran vgscan, lvscan showed the two active members, vgchange -vy set two active volume(s) in volume group "ubuntu-vg" now active, now mount /dev/ubuntu-vg/root /mnt mounted the volume to /mnt and chroot /mnt got me there.... !!

Now when I look in to the /boot directory its empty. What should be there and how can I add it??

Thanks so much
Jim

---

### Post by oldfred on 2015-07-16
I think when Boot-Repair does a full install & reinstall of grub, It also runs the command to make sure you have newest kernel.

If you do it manually I think it is better to do the full chroot.
These have standard paths, not your /mapper, so you need to make sure it is mounted as you have shown above.
 drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Then you can run a full set of updates while in chroot.
      
 #Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get autoremove
# fix Broken packages -f 
apt-get -f install
apt-get upgrade #newest versions of all packages, update must be run first
 apt-get install grub-pc grub-common #for BIOS based system, not UEFI
grub-install /dev/sda


#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
dpkg --configure -a

   sudo update-initramfs -k all -c
sudo update-grub

---

### Post by jim97 on 2015-07-16
oldfred

  Been trying to get networking going.  Finally got it by editing the /run/resolvconf/resolv.conf and adding my nameservers ip.   Just ran a apt-get update...hope that didn't screw anything up.
  Will now follow your post above and try the Boot-Repair.   

Thanks again

Jim

---

### Post by oldfred on 2015-07-17
I have not used Boot-Repair for a full uninstall/reinstall of grub, but I think it in effect walks you thru the chroot & update. It may not run or have you run all the commands I posted, but all may not be absolutely needed.

---

### Post by jim97 on 2015-07-17
Dropped down to  Chroot item  #4  and ran the apt-get purge grub grub-pc grub-common.   Got errors that no grub existed so Not Purged.   Okay I'll try installing it. 
ran apt-get -f install grub grub-pc grub-common  still got errors saying that they will not be installed.  Ran apt-get -f     first error was "can not write /dev/pts  is /dev mountd"   yes its mounted.   other errors appear   grep:  /proc/cpuinfo:  no such file / directory   

Well I was trying to copy the text of the out put of the apt-get -f install  command when the computer locked... opps shes back.

Here's the output of the above command.
```
root@ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-46 linux-headers-3.13.0-46-generic
  linux-headers-3.13.0-48 linux-headers-3.13.0-48-generic
  linux-headers-3.13.0-49 linux-headers-3.13.0-49-generic
  linux-headers-3.13.0-52 linux-headers-3.13.0-52-generic
  linux-headers-3.13.0-53 linux-headers-3.13.0-53-generic
  linux-headers-3.13.0-55 linux-headers-3.13.0-55-generic
  linux-image-3.13.0-46-generic linux-image-3.13.0-48-generic
  linux-image-3.13.0-49-generic linux-image-3.13.0-52-generic
  linux-image-3.13.0-53-generic linux-image-3.13.0-55-generic
  linux-image-extra-3.13.0-46-generic linux-image-extra-3.13.0-48-generic
  linux-image-extra-3.13.0-49-generic linux-image-extra-3.13.0-52-generic
  linux-image-extra-3.13.0-53-generic linux-image-extra-3.13.0-55-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.13.0-55-generic linux-image-3.13.0-57-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.13.0-55-generic linux-image-3.13.0-57-generic
0 upgraded, 2 newly installed, 0 to remove and 251 not upgraded.
11 not fully installed or removed.
Need to get 0 B/29.4 MB of archives.
After this operation, 65.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
E: Can not write log (Is /dev/pts mounted?) - openpty (2: No such file or directory)
(Reading database ... 501083 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-57-generic_3.13.0-57.95_i386.deb ...
grep: /proc/cpuinfo: No such file or directory
This kernel does not support a non-PAE CPU.
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-57-generic_3.13.0-57.95_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
Preparing to unpack .../linux-image-3.13.0-55-generic_3.13.0-55.94_i386.deb ...
grep: /proc/cpuinfo: No such file or directory
This kernel does not support a non-PAE CPU.
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-55-generic_3.13.0-55.94_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-55-generic /boot/vmlinuz-3.13.0-55-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-55-generic /boot/vmlinuz-3.13.0-55-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-57-generic_3.13.0-57.95_i386.deb
 /var/cache/apt/archives/linux-image-3.13.0-55-generic_3.13.0-55.94_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# 
```


I am afraid most of this is above me.  I am heading for bed, will check back tomorrow after-noon.

Thanks
Jim

---

### Post by jim97 on 2015-07-17
oldfred

   Sorry but I am having some problems posting and staying current with your posts.   Your last post #12 I didn't see last night,  I will run all the commands in post #10 later today and will post back.

Thanks
Jim

---

### Post by jim97 on 2015-07-17
oldfred

  Ran the first two commands off this morning before leaving.  

root@ubuntu:/# df -H
df: &#8216;/sys/fs/cgroup&#8217;: No such file or directory
df: &#8216;/sys/kernel/security&#8217;: No such file or directory
df: &#8216;/run/user&#8217;: No such file or directory
df: &#8216;/sys/fs/pstore&#8217;: No such file or directory
df: &#8216;/proc/sys/fs/binfmt_misc&#8217;: No such file or directory
df: &#8216;/sys/fs/cgroup/systemd&#8217;: No such file or directory
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root   28G   22G  4.4G  84% /
udev                          28G   22G  4.4G  84% /dev
tmpfs                         28G   22G  4.4G  84% /run
none                          28G   22G  4.4G  84% /run/lock
none                          28G   22G  4.4G  84% /run/shm
root@ubuntu:/# cat /etc/issue
Ubuntu 14.04.1 LTS \n \l

Looks like there is something wrong in the df -H command.

Thanks
Jim

---

### Post by tgalati4 on 2015-07-17
You can delete all of the kernels in linux on a system, including the one that you are running.  Just don't reboot.  It's a one-shot deal.

To repair, you need to reinstall the kernels, but this is not easy.

Your /boot might look like:

> tgalati4@Mint17 /boot $ ls -la
total 38908
drwxr-xr-x  3 root root     4096 Jun  1 11:39 .
drwxr-xr-x 23 root root     4096 Dec 19  2014 ..
-rw-r--r--  1 root root  1158016 May  2  2014 abi-3.13.0-24-generic
-rw-r--r--  1 root root   165510 May  2  2014 config-3.13.0-24-generic
drwxr-xr-x  5 root root     4096 Jul  3 07:15 grub
-rw-r--r--  1 root root 28803737 Jun  1 11:39 initrd.img-3.13.0-24-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3372643 May  2  2014 System.map-3.13.0-24-generic
-rw-------  1 root root  5776416 May  2  2014 vmlinuz-3.13.0-24-generic


---

### Post by tgalati4 on 2015-07-17
You can delete all of the kernels in linux on a system, including the one that you are running.  Just don't reboot.  It's a one-shot deal.

To repair, you need to reinstall the kernel, but this is not easy.

Your /boot might look like:

> tgalati4@Mint17 /boot $ ls -la
total 38908
drwxr-xr-x  3 root root     4096 Jun  1 11:39 .
drwxr-xr-x 23 root root     4096 Dec 19  2014 ..
-rw-r--r--  1 root root  1158016 May  2  2014 abi-3.13.0-24-generic
-rw-r--r--  1 root root   165510 May  2  2014 config-3.13.0-24-generic
drwxr-xr-x  5 root root     4096 Jul  3 07:15 grub
-rw-r--r--  1 root root 28803737 Jun  1 11:39 initrd.img-3.13.0-24-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3372643 May  2  2014 System.map-3.13.0-24-generic
-rw-------  1 root root  5776416 May  2  2014 vmlinuz-3.13.0-24-generic


Rather than trying to patch this system, I would backup your important data and perform a fresh install.  Even a newer version of Ubuntu if you want.  Otherwise, you will spend a lot of time trying to learn how to swim when you really just want to get out of the water.

It's a good idea to keep the current kernel and at least one backup kernel.

---

### Post by steeldriver on 2015-07-17
If you want to persevere with the chroot, then based on your df output it looks like you only bind-mounted /dev - iirc you need to do /proc, /sys, and /run as well (you won't see /run in many chroot guides, however it is necessary on  modern systems for internet connectivity because resolv.conf is  symlinked there). 

In your case, because you have a separate boot  partition, you will also need to mount that AFTER activating and  mounting the root VG


[NB all the following to be run as root, either by preceding each command with sudo or by entering an interactive root shell using 'sudo -i' at the start]

```

vgchange -ay /dev/mapper/ubuntu--vg-root

mount /dev/mapper/ubuntu--vg-root /mnt

mount /dev/sda1 /mnt/boot

mount -o bind /dev /mnt/dev

mount -o bind /proc /mnt/proc

mount -o bind /run /mnt/run

mount -o bind /sys /mnt/sys

```

THEN run the chroot command

```

chroot /mnt

```

---

### Post by oldfred on 2015-07-17
You do need all the system partitions mounted that a chroot requires, If an error that needs to be resolved first. And you have to have network running often needing the copy of resolv.conf.

Errors on files missing would be normal because you already deleted them. And if you manually deleted grub & kernels that leads to dpkg list of installed apps getting confused. The reinstall should fix that.

I just do not know LVM enough to be able to post detailed commands. But you have to modify standard mounts to include /mapper & LVM always has the separate /boot so you have to include that.

update:
I see steeldriver posted details. But chroot commands I have seen also include:
      mount --bind /dev/pts /mnt/dev/pts

And I have seen with -o on mount -o bind or mount --bind. I think either works.

---

### Post by jim97 on 2015-07-17
oldfred, steeldriver,  tgalati4

Well I gave it another try.  Below are the results.

ubuntu@ubuntu:~$ sudo -i

root@ubuntu:~# vgchange -ay /dev/mapper/ubuntu--vg-root
  Invalid volume group name: ubuntu-vg/root
  Run `vgchange --help' for more information.
root@ubuntu:~# 

everytime I have tried the above command I got the same error.   So I used the following commands.

root@ubuntu:~# vgchange -ay
  2 logical volume(s) in volume group "ubuntu-vg" now active
root@ubuntu:~# ls /mnt

root@ubuntu:~# mount  /dev/ubuntu-vg/root /mnt

root@ubuntu:~# ls /mnt
bin   cdrom  etc   lib         media  opt   root  sbin  sys  usr
boot  dev    home  lost+found  mnt    proc  run   srv   tmp  var

root@ubuntu:~# mount /dev/sda1 /mnt/boot

root@ubuntu:~# mount -o bind /dev /mnt/dev
root@ubuntu:~# mount -o bind /proc /mnt/proc
root@ubuntu:~# mount -o bind /run /mnt/run
root@ubuntu:~# mount -o bind /sys /mnt/sys

root@ubuntu:~# chroot /mnt

root@ubuntu:/# df -H
df: &#8216;/sys/fs/cgroup/systemd&#8217;: No such file or directory
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root   28G   22G  4.4G  84% /
udev                         780M  4.1k  780M   1% /dev
tmpfs                        159M  1.2M  157M   1% /run
none                         159M  1.2M  157M   1% /run/lock
none                         159M  1.2M  157M   1% /run/shm
none                         159M  1.2M  157M   1% /run/user

Better but there is still the "&#8216;/sys/fs/cgroup/systemd&#8217;: No such file or directory"  I've tried this several times with the same error.

Will this error stop everthing or can I still try the Boot-Repair??

Thanks Guys
Jim

---

### Post by jim97 on 2015-07-17
steeldriver, oldfred

Went back to oldfred's post #10 and followed the link to Boot-Repair,  when to step 4 again and had errors on the purge command so followed the 
apt-get -f install  command.  results below
root@ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-46 linux-headers-3.13.0-46-generic
  linux-headers-3.13.0-48 linux-headers-3.13.0-48-generic
  linux-headers-3.13.0-49 linux-headers-3.13.0-49-generic
  linux-headers-3.13.0-52 linux-headers-3.13.0-52-generic
  linux-headers-3.13.0-53 linux-headers-3.13.0-53-generic
  linux-headers-3.13.0-55 linux-headers-3.13.0-55-generic
  linux-image-3.13.0-46-generic linux-image-3.13.0-48-generic
  linux-image-3.13.0-49-generic linux-image-3.13.0-52-generic
  linux-image-3.13.0-53-generic linux-image-3.13.0-55-generic
  linux-image-extra-3.13.0-46-generic linux-image-extra-3.13.0-48-generic
  linux-image-extra-3.13.0-49-generic linux-image-extra-3.13.0-52-generic
  linux-image-extra-3.13.0-53-generic linux-image-extra-3.13.0-55-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.13.0-55-generic linux-image-3.13.0-57-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.13.0-55-generic linux-image-3.13.0-57-generic
0 upgraded, 2 newly installed, 0 to remove and 251 not upgraded.
11 not fully installed or removed.
Need to get 0 B/29.4 MB of archives.
After this operation, 65.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
E: Can not write log (Is /dev/pts mounted?) - openpty (2: No such file or directory)
(Reading database ... 501083 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-57-generic_3.13.0-57.95_i386.deb ...
Done.
Unpacking linux-image-3.13.0-57-generic (3.13.0-57.95) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-57-generic_3.13.0-57.95_i386.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.13.0-57-generic' to '/boot/vmlinuz-3.13.0-57-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
Preparing to unpack .../linux-image-3.13.0-55-generic_3.13.0-55.94_i386.deb ...
Done.
Unpacking linux-image-3.13.0-55-generic (3.13.0-55.94) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-55-generic_3.13.0-55.94_i386.deb (--unpack):
 cannot copy extracted data for './boot/config-3.13.0-55-generic' to '/boot/config-3.13.0-55-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-55-generic /boot/vmlinuz-3.13.0-55-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-55-generic /boot/vmlinuz-3.13.0-55-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-57-generic_3.13.0-57.95_i386.deb
 /var/cache/apt/archives/linux-image-3.13.0-55-generic_3.13.0-55.94_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks
Jim

---

### Post by oldfred on 2015-07-18
It seems like you are not mounting /dev/pts as it keeps giving that error.
Are you sure you have it mounted?
All the chroot examples show the mount of it also.

And error an uninstalling grub is correct as you have nothing to uninstall.

---

### Post by jim97 on 2015-07-18
Changing directory to /dev/pts works.
Trying to reinstall (apt-get -f install) seems to get a "failed to write (No space left on device)" error.
1      1049kB  256MB   255MB   primary   ext2         boot -  looks very small at 255mb

Jim

---

### Post by oldfred on 2015-07-18
There are many posts where users with LVM and default size of /boot gets full.
System does not automatically houseclean old kernels. That setting may now have been changed.
But users should only keep a couple of kernels and then the /boot is plenty large.

New systems seem to also have for UEFI signed & unsigned or other versions of kernels which then causes a /boot to fill up faster.

Or housecleaning is required regularly.
       Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

   RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

            With 14.04 this should keep two kernels on new kernel installs:
/etc/kernel/postinst.d/apt-auto-removal

            Determine your current kernel:
uname -a
-s is similate so you can review first:
sudo apt-get -s autoremove
sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by jim97 on 2015-07-18
oldfred

  /dev/pts was not mountd.   Exited chroot,  mount -o bind /dev/pts  /mnt/dev/pts.   chroot /mnt    and still getting errors when running apt-get -f  install,  about size.
  Getting close to throwing in the towel and reloading everything.

Thanks
Jim

---

### Post by oldfred on 2015-07-18
Sometimes it is quicker to reinstall, if you have good backups.
If you have deleted everything from /boot, I do not understand why it now has space issues?

If going back in with chroot:
df -h

---

### Post by jim97 on 2015-07-18
Okay,  the deed is done.  I started a fresh install at 12:20  pacific time.

Thanks so much to all of you who tried to get me thru this mess.  But a fresh start is easier then a college education.

Jim

---

### Post by jim97 on 2015-07-19
Well just to put a bow on this pig,  I have reloaded with lubuntu 15.04 and am very happy with its performance.  
The disk structure is completely different then the previous system so hopefully no more problems with the /boot directory filling up.

Much thanks to all those who tried to impart some sense to me.   I am sure you could have mastered it with a better tool / fool.

Thanks all
Jim

---

### Post by oldfred on 2015-07-19
Glad you got it working. :)

---

