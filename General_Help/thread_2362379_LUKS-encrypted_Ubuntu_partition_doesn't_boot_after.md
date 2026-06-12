---
title: "LUKS-encrypted Ubuntu partition doesn't boot after update-grub command"
date: 2017-05-27
forum: General Help
---

### Post by tom197 on 2017-05-27
I edited the GRUB_CMDLINE_LINUX parameter in /etc/default/grub in the attempt to solve a problem with corrupt desktop icons after resuming from hibernate. I used the fix described in this post:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1358936/comments/4](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1358936/comments/4)

Following the grub-update, my PC doesn't boot any more. After the grub menu I get a black screen with a blinking cursor. When the system was booting properly I did not see any grub menu, as the first screen to appear was the prompt to enter the password to decrypt my LUKS-encrypted partition.

Now the boot seems to stop before the LUKS password prompt and it freezes there.

I made a live USB disk with Ubuntu Gnome 16.04 and, through the "Disk" system application, I can "unlock" the encrypted partition by entering my pass-phrase. Unfortunately the home folder content of the partition is still unavailable (the home folder icon shows an "x"). I reckon that it is still locked somehow.

I can open /etc/default/grub in read-only mode, but I cannot edit the changes I made to the GRUB_CMDLINE_LINUX parameter and run the update-grub command to revert to the original state. Is there a way to edit this file from the live USB? Do I need some superuser privilege for that or to access the content of my home folder?

My preference is to repair the partition and make it boot correctly. Failing that, my second best solution would be to access my home folder and backup the data there before formatting and re-installing the system again.

From the live USB I even installed the Boot-Repair application and run it, but it didn't restore my boot.

Thank you very much for any help you can give me.

---

### Post by yancek on 2017-05-27
You need to be root (use sudo) to make those kind of changes.  Make sure you are using the /etc/default/grub file on the hard drive by accessing it from the /media/ubuntu directory.  Usually they are listed by UUID.  Running update-grub from the flash drive won't help as that updates the live system on the flash and is lost on reboot.  Use the chroot method described at the Ubuntu site at the link below, Section 2.2.5.

---

### Post by tom197 on 2017-05-28
> **yancek said:**
> Use the chroot method described at the Ubuntu site at the link below, Section 2.2.5.

Could you please provide the link to the chroot method you mention? I cannot see it in your post.

Thank you.

---

### Post by yancek on 2017-05-28
> Could you please provide the link to the chroot method you mention? I cannot see it in your post.

Sorry about that, link below.

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by tom197 on 2017-05-29
I tried the suggested chroot method suggested above, without success. Here is what I did: 

sudo fdisk -l /dev/sda

Disk /dev/sda: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x495d78fa

Device     Boot   Start       End   Sectors  Size Id Type
/dev/sda1  *       2048    999423    997376  487M 83 Linux
/dev/sda2       1001470 500117503 499116034  238G  5 Extended
/dev/sda5       1001472 500117503 499116032  238G 83 Linux



sudo blkid

/dev/sda1: UUID="dffaa40c-b9c4-4afa-8a4b-a11ed066c82e" TYPE="ext2" PARTUUID="495d78fa-01"
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="d7156cd6-2eba-47b8-bc8a-92173e834b94" TYPE="crypto_LUKS" PARTUUID="495d78fa-05"
/dev/sdb1: UUID="2017-02-15-20-49-53-00" LABEL="Ubuntu-GNOME 16.04.2 LTS amd64" TYPE="iso9660" PTUUID="2e8e75d1" PTTYPE="dos" PARTUUID="2e8e75d1-01"
/dev/sdb2: SEC_TYPE="msdos" UUID="E561-C446" TYPE="vfat" PARTUUID="2e8e75d1-02"


df -Th

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.8G     0  3.8G   0% /dev
tmpfs          tmpfs     769M  9.5M  759M   2% /run
/dev/sdb       iso9660   1.3G  1.3G     0 100% /cdrom
/dev/loop0     squashfs  1.2G  1.2G     0 100% /rofs
aufs           aufs      3.8G  267M  3.5G   7% /
tmpfs          tmpfs     3.8G   59M  3.7G   2% /dev/shm
tmpfs          tmpfs     5.0M  8.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.8G     0  3.8G   0% /sys/fs/cgroup
tmpfs          tmpfs     3.8G     0  3.8G   0% /tmp
tmpfs          tmpfs     769M   36K  768M   1% /run/user/999


sudo mount /dev/sda5 /mnt
mount: unknown filesystem type 'crypto_LUKS'


Since I was stuck there I browsed the Internet and found these steps to unlock the encrypted partition:
[https://blog.sleeplessbeastie.eu/2015/11/16/how-to-mount-encrypted-lvm-logical-volume/](https://blog.sleeplessbeastie.eu/2015/11/16/how-to-mount-encrypted-lvm-logical-volume/)


sudo cryptsetup luksOpen /dev/sda5 myhd
Enter passphrase for /dev/sda5: 

sudo vgdisplay --short
  "ubuntu-gnome-vg" 237.99 GiB [237.95 GiB used / 44.00 MiB free]

sudo lvs -o lv_name,lv_size -S vg_name=ubuntu-gnome-vg
  LV     LSize  
  root   230.25g
  swap_1   7.70g


sudo lvchange -ay ubuntu-gnome-vg/root

sudo mkdir /media/myhd_mount_point

sudo mount /dev/ubuntu-gnome-vg/root /media/myhd_mount_point

sudo mount /dev/mapper/myhd /mnt
mount: unknown filesystem type 'LVM2_member'

After I got stuck again I found out that my home/$USER folder only contains two files:

Access-Your-Private-Data.desktop
README.txt

The latter reads:
[I]
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private[/I]


I tried the ecryptfs-mount-private command, but I got the following error:

ERROR: Encrypted private directory is not setup properly


After two days of frustrating attempts, I am still stuck without the ability to access the content of my home folder or update-grub to restore the correct boot.    :(

---

