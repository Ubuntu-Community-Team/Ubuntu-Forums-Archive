---
title: "[SOLVED] Error 17, 22 in GRUB...partitioning too"
date: 2008-07-04
forum: General Help
---

### Post by fiddler616 on 2008-07-04
Hey,
A few weeks ago, I decided to become a man and install Ubuntu on my Sony Vaio laptop--dual-booting it with Windows XP (OK, half-a-man). After quite a few speedbumps, it got installed, and I've been using it happily since...well, not quite.
I have a 40 GB ATA hard drive (let me know if you want to know more--that's all I know off the top of my head), which came partitioned in C:\ and D:\.
After installing Ubuntu, C:\ was left intact (FYI-it has Windows on it), and D:\ was wiped, reformatted into Ext3, and had Ubuntu installed. I also made a one gig swap partition (while we're here--is that a good size?). D:\ is about 19 GBs big, and it previously had a lot of Windows-specific Program Files on it. I didn't know how big to make it when installing Ubuntu, so I just kept it at 19-odd, and now have no space for my Program Files.
So today, using Windows (that was the first tutorial I found online), I cut it down a bit, and used the "unallocated space" to make an NTFS partition. I continued about my business, and eventually shut down. Then I tried to reboot and...Grub 1.5 loading...Error 17.
So I whipped out the Ubuntu live CD (I do NOT have the Windows one), used the "try" feauture to get help, ended up re-installing GRUB, rebooted, and got the OS selection screen.
==Now the problems start==
* There are TWO Ubuntu 8.04/Ubuntu 8.04 recovery mode entires apiece.
* When I try to enter Ubuntu/recovery mode/the other Ubuntu/ the other recovery mode/memtest (only one of those), it gives me Error 17, and says it can't mount the partition.
* When I try to enter Windows XP, it gives me Error 22, and says there is "no partition" (Direct quote) (?????)
==End problems==
So here I am running Ubuntu off a CD, and am at my wit's end, having Googled everything I can think of.
I can post more info if you want, I'm just not sure what you do want...(I'm still a bit new at this)

Edit:
I've been to [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113) and did this:> 1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.
And it did nothing.
And I HAVEN'T done this:
> 1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
because I've never seen [!!!] Disk Partition.

---

### Post by logos34 on 2008-07-04
> **fiddler616 said:**
> because I've never seen [!!!] Disk Partition.

That's on the text-based alternate install cd, not the livecd.

If you used something like Acronis or Partition Magic to resize ubuntu, maybe it didn't do filesystem check afterward.  That could be the problem.  In any case it's easy to do and the most obvious thing to try first.  

First, post your fdisk:

**sudo fdisk -l**

Then run this command:

**sudo fsck /dev/sda2** (or whatever root partition is)

Then mount your root partition and post your **/boot/grub/menu.lst**--maybe there's an error.  

About the extra kernels: did you perhaps update recently?  There have been numerous kernel updates (latest is -19).

---

### Post by fiddler616 on 2008-07-05
> First, post your fdisk:

sudo fdisk -l
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5827c934

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         122      979933+  82  Linux swap / Solaris
/dev/sda3   *         654        2476    14643247+   7  HPFS/NTFS
/dev/sda4            2477        4864    19181610   83  Linux

```
> Then run this command:

sudo fsck /dev/sda2```

ubuntu@ubuntu:~$ sudo fsck /dev/sda4
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda4: clean, 130875/1199520 files, 798782/4795402 blocks
ubuntu@ubuntu:~$ 
```

On **/bootgrub/menu.lst**, forgive my noobness, but I didn't intuitively know how to mount in a terminal, so I went to this: [http://ubuntuforums.org/archive/index.php/t-647568.html](http://ubuntuforums.org/archive/index.php/t-647568.html) which also was about displaying menu.lst, tried everything they tried, and kept getting error messages: [note: I also did find /boot/brug/menu.lst in the grub prompt, which didn't work.
```
find /boot/grub/menu.lst
find: /boot/grub: No such file or directory
ubuntu@ubuntu:~$ mount /boot/grub/menu.lst
mount: can't find /boot/grub/menu.lst in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ sudo mount /dev/sda4 ubuntu
mount: mount point ubuntu does not exist
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo mount -t reiserfs /dev/sda4 ubuntu
mount: mount point ubuntu does not exist
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo mkdir /ubuntu
ubuntu@ubuntu:~$ sudo mount -t reiserfs /dev/sda4 /ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -t proc none /ubuntu/proc
mount: mount point /ubuntu/proc does not exist
ubuntu@ubuntu:~$ sudo mount -o bind /dev /ubuntu/dev
mount: mount point /ubuntu/dev does not exist
ubuntu@ubuntu:~$ sudo chroot /ubuntu
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

ubuntu@ubuntu:~$ 

```
I also tried this:
```
ubuntu@ubuntu:~$ grub-install
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.
```
but got scared off because I didn't know if I wanted it in root or DIR.

As for updating, I did update like a week ago, but am *pretty* sure I've used GRUB succesfully since then.

Thanks for your help so far.

---

### Post by fiddler616 on 2008-07-05
I went to /boot/grub/menu.lst just in the File Browser, no terminals involved, and got as far as /boot --there was no grub folder in it, just some text documents, a .bak file, a .bin file, and a "unkown" file. The folder included file names with stuff like:
abi-numbers
config-numbers
initrd.img-numbers-generic.bak
memtest86+.bin
System.map-(numbers)-generic
vmlinuz(sic)-numbers-generic 

All of the numbers are 2.6.24-16

...Don't know if that helps or not...

---

### Post by caljohnsmith on 2008-07-05
> **fiddler616 said:**
> I went to /boot/grub/menu.lst just in the File Browser, no terminals involved, and got as far as /boot --there was no grub folder in it, just some text documents, a .bak file, a .bin file, and a "unkown" file. The folder included file names with stuff like:
abi-numbers
config-numbers
initrd.img-numbers-generic.bak
memtest86+.bin
System.map-(numbers)-generic
vmlinuz(sic)-numbers-generic 

All of the numbers are 2.6.24-16

...Don't know if that helps or not...
Sounds like somehow Grub wasn't properly installed. Just boot the Live CD again, and do the following from a terminal window:
```
sudo mkdir /mnt/sda4
sudo mount /dev/sda4 /mnt/sda4
sudo grub-install --root-directory=/mnt/sda4 /dev/sda --recheck
```
That should reinstall Grub. If that goes OK, do the following to create a menu.lst for Grub:
```
sudo chroot /mnt/sda4
sudo update-grub

```
If the above doesn't work, you'll have to reinstall the Grub package to that partition probably.

---

### Post by logos34 on 2008-07-05
with the hardy livecd all you have to do is click on the root volume in nautilus to mount it.

After you run grub-install as caljohnsmith suggested, navigate to /boot/grub and post your menu.lst so we can check it out.

From fdisk it looks like you shaved some space off windows partition at the front of the disk to make room for swap (you didn't use all of it apparently because there's some empty space between sda1 and sda3).  Also you say:

> D:\ is about 19 GBs big, and it previously had a lot of Windows-specific** Program Files** on it. I didn't know how big to make it when installing Ubuntu, so I just kept it at 19-odd, and now have no space for my Program Files.
So today, using Windows (that was the first tutorial I found online), I cut it down a bit, and used the "unallocated space" to make an NTFS partition.

Do you mean installed programs/applications, or windows system files?  

You might want to run **TestDisk** to fix any partition table errors.

---

### Post by fiddler616 on 2008-07-07
Thanks for all your help, and I feel like a complete tool saying this, but I got a little bit impatient, and realized that since I'd only had Ubuntu installed for two weeks, there really wasn't much to lose by just re-installing it from the live CD (this also helped let me make the exact partitions I wanted hassle-free).

Thanks again

---

