---
title: "Move /boot from own partition to main"
date: 2008-06-19
forum: General Help
---

### Post by cwacker on 2008-06-19
Hi, i have problems with mu /boot because ive made it to small and i can't increase the size of it, so i'm wondering if there is any way tomove it to the main partition... I've been searching around without finding any solutions to this :/

---

### Post by TeoBigusGeekus on 2008-06-19
You can increase the size of it - it's just that the partition needs to be unmounted first for any operations to take place.
Boot with the live cd and run gnome partition editor. Resize it from there.

---

### Post by avtolle on 2008-06-19
I've a feeling the OP is running into the resize from the end of the partition issue, and there isn't any room at the end of his /boot partition to add to it.

@OP: I don't know any way to accomplish that. [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) provides techniques you could use to make a new /boot partition which would be larger, and copy the contents from your existing one to it. If you are dual booting with XP or Vista, you probably should have a separate /boot partition anyway. IF you decide to create a new, larger /boot partition, you'll likely need to edit grub so it points at the right place to boot Ubuntu.

---

### Post by sisco311 on 2008-06-19
1.) unmount the partition:
```
sudo umount /boot
```2.) mount it under /mnt
```
sudo mount -t ext3 /dev/sdaX /mnt
```assuming sdaX is the /boot partition

3.) copy the files to the /boot directory
```
sudo cp -R /mnt/* /boot/
```4.) edit the fstab:
```
gksu gedit /etc/fstab
```and comment out the entry for the /boot partition:
> ...
[SIZE=4]**#**[/SIZE]UUID=xxxxxxxx-xxxx-xxxx-xxxxx-xxxxxxxxxxxx **/boot**     ext3    relatime,defaults        0       2
...5.) edit the menu.lst
 ```
gksu gedit /boot/grub/menu.lst
```> title        Ubuntu, kernel 2.6.20-15-generic
**root        (hd0,[COLOR=#009900][B]0**[/COLOR])[/B]
kernel      **/boot/**vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd       **/boot/**initrd.img-2.6.20-15-generic
quiet
savedefaultChange the **root** line to point to the / (root) partition.
[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

Make sure the path is correct in the kernel and initrd line.

---

### Post by cwacker on 2008-06-19
I have space on the drive, but it is all allocated.. The /boot is "in the middle" of thedrive (says gparted).  its something like this:

[NTFS win partition] [/boot][swap]["main ubuntu"]

This, of course, depends on gparted actally displaing the partiotions as they are "aligned"..

Am I clear enough? 

The problem is i cant dpkg --configure -a because of /boot being 100% full and i cant remove old kernelfiles because synaptic refuses to run without me doing a dpkg --configure -a... Kind of a moment 22.

---

### Post by sisco311 on 2008-06-19
> **cwacker said:**
> I have space on the drive, but it is all allocated.. The /boot is "in the middle" of thedrive (says gparted).  its something like this:

[NTFS win partition] [/boot][swap]["main ubuntu"]

This, of course, depends on gparted actally displaing the partiotions as they are "aligned"..

Am I clear enough? 

The problem is i cant dpkg --configure -a because of /boot being 100% full and i cant remove old kernelfiles because synaptic refuses to run without me doing a dpkg --configure -a... Kind of a moment 22.

post the error you get from 
```
sudo dpkg --configure -a
```IDEA: try to run dpkg --configure -a after step 3.

---

### Post by cwacker on 2008-06-19
This is the result from a sudo dpkg --configure -a 

Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not installed.
dpkg: error processing linux-restricted-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not installed.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not installed.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-19-generic; however:
  Package linux-ubuntu-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-19-generic; however:
  Package linux-restricted-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.19.21); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.19.21); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
 linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: subprocess post-installation script returned error exit status 1





ls -Rsh /boot gives me this:


/boot:
total 39M
416K abi-2.6.24-16-generic 7.2M initrd.img-2.6.24-17-generic.bak
416K abi-2.6.24-17-generic 12K lost+found
416K abi-2.6.24-18-generic 102K memtest86+.bin
80K config-2.6.24-16-generic 884K System.map-2.6.24-16-generic
80K config-2.6.24-17-generic 889K System.map-2.6.24-17-generic
80K config-2.6.24-18-generic 889K System.map-2.6.24-18-generic
1.0K grub 1.9M vmlinuz-2.6.24-16-generic
7.6M initrd.img-2.6.24-16-generic 1.9M vmlinuz-2.6.24-17-generic
7.1M initrd.img-2.6.24-16-generic.bak 1.9M vmlinuz-2.6.24-18-generic
7.2M initrd.img-2.6.24-17-generic

/boot/grub:
total 181K
1.0K default 9.0K jfs_stage1_5 10K reiserfs_stage1_5
1.0K device.map 6.0K menu.lst 1.0K stage1
8.0K e2fs_stage1_5 6.0K menu.lst~ 107K stage2
8.0K fat_stage1_5 5.0K menu.lst_bak 10K xfs_stage1_5
1.0K installed-version 8.0K minix_stage1_5

/boot/lost+found:
total 0



EDIT
In my GRUB menu i have kernel 16, 17 and 18. choosing 18 gives me a kernel panic error, 16 and 17 works fine.

---

### Post by plucky on 2008-06-19
> [NTFS win partition] [/boot][swap]["main ubuntu"]


What about moving the swap partition to the end of the drive and expanding /boot into the swap partition using gParted on the live CD.


Just a thought.

Good Luck

---

### Post by sisco311 on 2008-06-19
Try to move /boot/initrd.img-2.6.24-17-generic.bak(backup file) to the root partition. And run the dpkg command.

---

### Post by cwacker on 2008-06-19
So I think i will go with the "move my /boot to primary" solution instead since i couldnt free enough space...

my fstab is:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=8fa1e89c-1e97-474f-be5a-b614dce01747 /               ext3    relatime,errors=remount-ro 0       1
[B]# /dev/sda3
UUID=f78d65db-0107-4898-abd4-c6496e8aaf25 /boot           ext3    relatime        0       2[/B]
# /dev/sda5
UUID=ba470daa-5700-4b8d-9316-efa464a83d87 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

which makes me assume that /boot is located on sda3, correct?
that should make the step 2:
```
sudo mount -t ext3 /dev/sda3 /mnt
``` 
right? but why do i want to remount it? it's still 50 mb small?

I don't understand what step 3 is doing either, and what the point is with it. 
```
sudo cp -R /mnt/* /boot/
```

I'm quite sure I've missed something, but can you please explain the steps for me?


Thanks in advance!

---

### Post by avtolle on 2008-06-19
It needs to be mounted to copy from it, which is being done in the next step. The -R is for recursive, so that all files in the directory are copied to the new location, not just the directory itself.

---

