---
title: "Grub Bootup Question-Too many selections"
date: 2013-08-17
forum: General Help
---

### Post by aviator1 on 2013-08-17
As I mentioned in an earlier post, I just got this computer with Windows 7 (64). I had a bootup issue in that it would only boot to Windows. Through some forum help, I was able to get Boot-Repair to work and all was fine.

However, when I get to the screen that offers the choice of what to bootup (I think it's called the splash screen???), I get the "normal" choices at the top, then a huge list of other selections. More than a page full.

I don't know how to copy that page or take a screen shot during that period of the bootup.

The situation doesn't seem to affect performance.

Also, I didn't notice this until I downloaded some nvidia drivers if that makes a difference.

Thanks for any help or suggestions.

Regards,

Dave

---

### Post by Bashing-om on 2013-08-17
aviator1; Hi !
This is the procedure I use>
lookat at how many kernels are presently installed.
```

ls -la /boot

```
You MUST keep the kernel you are presently running on and always keep one backup kernel ...
```

uname -a ##in a terminal will tell you which kernel you are running....then:

```
Go to Synaptic Package Manager  select status on the left-lower  pane and select installed on the left-upper pane and search for linux-image.
 select the ones you want deleted. listed in the right-upperpane.
  and mark for complete removal.
Click the Apply button in the toolbar and then Apply in the summary window that pops up. Close Synaptic Package Manager.
And in terminal do:
```

sudo update-grub

```
  In addition to linux-image, also remove old versions of linux-headers and linux-restricted-modules (if you have them).

Do not forget to run: -> "sudo update-grub" !!!!!!! as it does all the background stuff to redo the grub menu.

see also:

[https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean)

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2013-08-17
You will need to see the different versions of vmlinuz in your /boot folder as they are the kernels, but the command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
``` will also show you what appears in your grub menu and you can then search for the numbered versions in synaptic, removing the linux-image packages and the same versions of whatever header packages you also have.  After removing kernels with synaptic you **do not** need to run **sudo update-grub**; that is done during the removal process automatically.

Just keep the most recent and the previous one.

---

### Post by aviator1 on 2013-08-17
Here's what I get. Is it a simple as deleting the extras?

dave@dave-desktop:~$ grep "menuentry" /boot/grub.cfg | cut -c 1-100
grep: /boot/grub.cfg: No such file or directory
dave@dave-desktop:~$ grep "menuentry" /boot/grub/grub.cfg | cut -c 1-100
menuentry 'Ubuntu, with Linux 3.5.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.5.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.5.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
menuentry "Ubuntu, with Linux 3.2.0-51-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-51-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-51-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-51-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-49-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-49-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-49-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-49-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-48-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-48-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-48-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-48-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-45-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-45-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-45-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-45-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-44-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-44-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-44-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-44-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-43-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-43-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-43-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-43-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-41-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-41-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-41-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-41-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-40-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-40-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-40-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-40-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-39-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-39-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-39-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-39-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-38-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-38-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-38-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-38-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-37-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-37-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-37-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-37-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-36-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-36-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-36-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-36-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-35-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-35-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-35-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-34-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-34-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-34-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-34-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-33-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-33-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-33-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-33-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-32-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-32-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-32-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-31-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-31-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-31-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-31-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-30-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-30-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-30-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-30-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.2.0-29-generic-pae (on /dev/sdb2)" --class gnu-linux --class gnu --c
menuentry "Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode) (on /dev/sdb2)" --class gnu-linux
menuentry "Ubuntu, with Linux 3.2.0-29-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.2.0-29-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 2.6.32-42-generic (on /dev/sdb2)" --class gnu-linux --class gnu --clas
menuentry "Ubuntu, with Linux 2.6.32-42-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --
menuentry "Ubuntu, with Linux 2.6.32-41-generic (on /dev/sdb2)" --class gnu-linux --class gnu --clas
menuentry "Ubuntu, with Linux 2.6.32-41-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --
menuentry "Ubuntu, with Linux 2.6.32-40-generic (on /dev/sdb2)" --class gnu-linux --class gnu --clas
menuentry "Ubuntu, with Linux 2.6.32-40-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --
menuentry "Ubuntu, with Linux 2.6.32-39-generic (on /dev/sdb2)" --class gnu-linux --class gnu --clas
menuentry "Ubuntu, with Linux 2.6.32-39-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --
menuentry "Ubuntu, with Linux 2.6.32-38-generic (on /dev/sdb2)" --class gnu-linux --class gnu --clas
menuentry "Ubuntu, with Linux 2.6.32-38-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --
menuentry "Ubuntu, with Linux 2.6.32-37-generic (on /dev/sdb2)" --class gnu-linux --class gnu --clas
menuentry "Ubuntu, with Linux 2.6.32-37-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --
menuentry "Ubuntu, with Linux 2.6.32-36-generic (on /dev/sdb2)" --class gnu-linux --class gnu --clas
menuentry "Ubuntu, with Linux 2.6.32-36-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --
menuentry "Ubuntu, with Linux 2.6.32-35-generic (on /dev/sdb2)" --class gnu-linux --class gnu --clas
menuentry "Ubuntu, with Linux 2.6.32-35-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --
menuentry "Ubuntu, with Linux 2.6.32-34-generic (on /dev/sdb2)" --class gnu-linux --class gnu --clas
menuentry "Ubuntu, with Linux 2.6.32-34-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --
menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sdb2)" --class gnu-linux --class gnu --clas
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdb2)" --class gnu-linux --class gnu --clas
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --
dave@dave-desktop:~$

---

### Post by aviator1 on 2013-08-17
Here's what I get with ls -la /boot

dave@dave-desktop:~$ ls -la /boot
total 53960
drwxr-xr-x  4 root root     4096 Aug 16 12:53 .
drwxr-xr-x 24 root root     4096 Aug 16 07:17 ..
-rw-r--r--  1 root root   848290 Jan 25  2013 abi-3.5.0-23-generic
-rw-r--r--  1 root root   852910 Jul 10 13:09 abi-3.5.0-37-generic
-rw-r--r--  1 root root   147880 Jan 25  2013 config-3.5.0-23-generic
-rw-r--r--  1 root root   148157 Jul 10 13:09 config-3.5.0-37-generic
drwxr-xr-x  3 root root    12288 Aug 16 12:42 grub
drwxr-xr-x  3 root root     4096 Aug 16 07:17 grub.bak
-rw-r--r--  1 root root 15546295 Aug 16 07:28 initrd.img-3.5.0-23-generic
-rw-r--r--  1 root root 15692338 Aug 16 12:53 initrd.img-3.5.0-37-generic
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  3023265 Jan 25  2013 System.map-3.5.0-23-generic
-rw-------  1 root root  3022033 Jul 10 13:09 System.map-3.5.0-37-generic
-rw-r--r--  1 root root  5189248 Aug 16 07:06 vmlinuz-3.5.0-23-generic
-rw-------  1 root root  5184992 Jul 10 13:09 vmlinuz-3.5.0-37-generic
-rw-------  1 root root  5186912 Aug 16 07:16 vmlinuz-3.5.0-37-generic.efi.signed

---

### Post by ajgreeny on 2013-08-17
Crikey! That is one long list of installed kernels.

However, I am wondering; do you have just the one installation of ubuntu or is there an older one on the machine?

Can we see the output of ```
sudo fdisk -l
``` please

---

### Post by Bashing-om on 2013-08-17
+1 with an added - Yikes!

Past time to do a bit of house cleaning.

---

### Post by aviator1 on 2013-08-17
> **ajgreeny said:**
> Crikey! That is one long list of installed kernels.

However, I am wondering; do you have just the one installation of ubuntu or is there an older one on the machine?

Can we see the output of ```
sudo fdisk -l
``` please


When I first attempted to load 12.04 next to Windows, I got a disk error during the load. I did another download of 12.04 and had a successful installation.

However, the computer would them only boot to Windows 7. A subsequent installation of boot-repair fixed that, and as I recall, the loader only had the "correct" choices at bootup.

I believe it was after the nvidia driver download that I found all this extra stuff. I don't know how that would have anything top do with this.

And, I did install the old HDD from my previous machine, which does have 12.04 on it, also. 

However, it was in before all this happened as well.

Thanks for any advice.


Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1cff2565

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1023999      510976    7  HPFS/NTFS/exFAT
/dev/sda2         1024000   250569727   124772864    7  HPFS/NTFS/exFAT
/dev/sda3       250570750   500117503   124773377    5  Extended
/dev/sda5       466767872   500117503    16674816   82  Linux swap / Solaris
/dev/sda6       250570752   466767871   108098560   83  Linux

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  1953514583+  ee  GPT
dave@dave-desktop:~$

---

### Post by Bashing-om on 2013-08-17
aviator1; Hey ...

Not making a lot of sense to me .. let's wait for AJ's input:
this:
> Linux 3.2.0-48-generic-pae (on /dev/sdb2)
with this:
> 
Device Boot Start End Blocks Id System
/dev/sdb1 1 3907029167 1953514583+ ee GPT
dave@dave-desktop:~$

I thought that fdisk had been updated to read GPT partitions (??) ... but;
The former output shows at least 2 partitions .. and many kernels installed onto sdb2 [operating systems installed onto sda drive]... and ... "fdisk" only shows the 2nd drive with only one partition ????

[INDENT][INDENT]is this a can of worms ?
[/INDENT][/INDENT]

---

### Post by aviator1 on 2013-08-17
It probably started with the aborted install..........

However, I did a couple of good boots after running boot-repair without the mess.

I'm early enough into this that I could uninstall/install without losing much.

I really apreciate your help.

Regards,

Dave

---

### Post by Bashing-om on 2013-08-17
aviator1;

I do not consider that situation dire to the point of even thinking about (re-)installing . Presently all we are looking at is cleaning up the 2nd drive (sdb)...which all those reference to old kernels on sdb2 may only reside in a config file .. with nothing in actuality.
Still await AJ's advise ... as I have no experience with GPT partitions, or the tools to look at it ..

Your system is stable .. just needs a bit of clean up.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by aviator1 on 2013-08-17
Thanks.

I'll be patient. Have a good evening.

Regards,

Dave

---

### Post by deadflowr on 2013-08-18
> **Bashing-om said:**
> aviator1;

I do not consider that situation dire to the point of even thinking about (re-)installing . Presently all we are looking at is cleaning up the 2nd drive (sdb)...which all those reference to old kernels on sdb2 may only reside in a config file .. with nothing in actuality.
Still await AJ's advise ... as I have no experience with GPT partitions, or the tools to look at it ..

Your system is stable .. just needs a bit of clean up.
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]



```
sudo parted -l
```

Will let you look at GPT partitions, where as fdisk cannot.

---

### Post by aviator1 on 2013-08-18
Here is what sudo parted -l shows:

Model: ATA M4-CT256M4SSD2 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  524MB  523MB   primary   ntfs            boot
 2      524MB   128GB  128GB   primary   ntfs
 3      128GB   256GB  128GB   extended
 6      128GB   239GB  111GB   logical   ext4
 5      239GB   256GB  17.1GB  logical   linux-swap(v1)


Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2097kB  1049kB
 2      2097kB  1021GB  1021GB  ext4
 4      1021GB  1021GB  1049kB                        bios_grub
 5      1021GB  1982GB  961GB   ext4
 6      1982GB  1991GB  9281MB  linux-swap(v1)
 3      1991GB  2000GB  9282MB  linux-swap(v1)


dave@dave-desktop:~$

---

### Post by Bashing-om on 2013-08-18
aviator1; Look's like I can comprehend now ..

@deadflower .. thanks for the clarification !

A bit of cleanup ... You have 3 swap partitions .. only one is needed , the other two may be done away with and reused to better purpose;
remove all but 2 kernels from the sdb2 install(s), and same for the ubuntu sda install.

Let's look at what and how you are booting ... and the UUID assignments.  Are you able to boot up all of the operating systems from either of the hard drives ?
Post the output of terminal codes:
```

sudo blkid
cat /etc/fstab

```
And we can do this.
[INDENT][INDENT][INDENT]just another process
[/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2013-08-18
It is my guess that Ubuntu on the old hard disk (now sdb) is 12.04 with Grub 1.99 and Ubuntu on sda is a later version of 12.04, possibly 12.04.1 or 12.04.2 and it comes not only with the Ubuntu 12.10 linux kernel (3.5.0-37) but also with Grub 2.0. The mess you are seeing is the mess we get when these two versions of Grub collide. I am also guessing that the Grub in control of booting is the one on sdb. Grub 1.99 cannot understand the submenus in Grub 2.0. In my way of thinking.

The first step is to use Synaptic to remove most of those kernels from Ubuntu on sdb from kernel 2.6.32-28 to kernel 3.2.0-48. Leave just kernels 3.2.0-49 and 3.2.0-51. That will remove a lot of the mess.

The second step is to boot into Ubuntu on sda and run

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

That will put Grub 2.0 into the MBR of sda and most of those previous kerenls will disappear into the Advanced Options submenu.

Another solution would be to put Grub 2.0 on both versions of Ubuntu 12.04 by this PPA

[https://launchpad.net/~cjwatson/+archive/grub](https://launchpad.net/~cjwatson/+archive/grub)

Colin Watson is the main developer who worked on getting Grub 2.0 into Ubuntu and sorted out the issues we were having when 12.10 was under development and Grub 2.0 came into Ubuntu.

Regards.

---

### Post by ajgreeny on 2013-08-18
I think grahammechanical is right, but I would also like to know which is the OS that you are actually using when you boot into ubuntu.  Can you please show us the output of command ```
mount
``` which will tell us which partition is your running root, along with any others that are mounted, eg /swap, /efi and a separate /home, if you have one.  The output of ```
cat /etc/fstab
``` would also be very useful. Knowing that we can tell you which partitions you can safely delete and use for other purposes.

Incidentally, in my Xubuntu 12.04.2 64bit system which I have on UEFI system I still have grub 1.99, not grub 2, and it looks as if that ppa suggested will not update my system to grub 2 as with a UEFI system and /efi partition being used, I do not have the package the ppa supplies (grub2) installed.

---

### Post by Bashing-om on 2013-08-18
As an aside ... on my system I am triple booting ... and I have 13.04 playing real nicely now with other 12.04 versions' grubs.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by aviator1 on 2013-08-19
> **ajgreeny said:**
> I think grahammechanical is right, but I would also like to know which is the OS that you are actually using when you boot into ubuntu.  Can you please show us the output of command ```
mount
``` which will tell us which partition is your running root, along with any others that are mounted, eg /swap, /efi and a separate /home, if you have one.  The output of ```
cat /etc/fstab
``` would also be very useful. Knowing that we can tell you which partitions you can safely delete and use for other purposes.

Incidentally, in my Xubuntu 12.04.2 64bit system which I have on UEFI system I still have grub 1.99, not grub 2, and it looks as if that ppa suggested will not update my system to grub 2 as with a UEFI system and /efi partition being used, I do not have the package the ppa supplies (grub2) installed.

Mount shows:

dave@dave-desktop:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/dave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dave)

cat /etc/ftab shows:

dave@dave-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=75e89545-dc5c-4553-907d-23269bb7b2a9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=80d61814-fc43-4c38-b772-d32945f6b4a1 none            swap    sw              0       0

---

### Post by aviator1 on 2013-08-19
> **grahammechanical said:**
> It is my guess that Ubuntu on the old hard disk (now sdb) is 12.04 with Grub 1.99 and Ubuntu on sda is a later version of 12.04, possibly 12.04.1 or 12.04.2 and it comes not only with the Ubuntu 12.10 linux kernel (3.5.0-37) but also with Grub 2.0. The mess you are seeing is the mess we get when these two versions of Grub collide. I am also guessing that the Grub in control of booting is the one on sdb. Grub 1.99 cannot understand the submenus in Grub 2.0. In my way of thinking.

The first step is to use Synaptic to remove most of those kernels from Ubuntu on sdb from kernel 2.6.32-28 to kernel 3.2.0-48. Leave just kernels 3.2.0-49 and 3.2.0-51. That will remove a lot of the mess.

The second step is to boot into Ubuntu on sda and run

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

That will put Grub 2.0 into the MBR of sda and most of those previous kerenls will disappear into the Advanced Options submenu.

Another solution would be to put Grub 2.0 on both versions of Ubuntu 12.04 by this PPA

[https://launchpad.net/~cjwatson/+archive/grub](https://launchpad.net/~cjwatson/+archive/grub)


Colin Watson is the main developer who worked on getting Grub 2.0 into Ubuntu and sorted out the issues we were having when 12.10 was under development and Grub 2.0 came into Ubuntu.

Regards.

The above referenced codes had no affect on the situation. I will review the link you included. 

I was, however, able to boot to the "old" disk with no problem by disconnecting the new disk.

When I reconnected the new disk, the same problems arose.

Thank you very much. I will get to it sometime today.

Dave

---

### Post by aviator1 on 2013-08-19
> **Bashing-om said:**
> aviator1; Look's like I can comprehend now ..

@deadflower .. thanks for the clarification !

A bit of cleanup ... You have 3 swap partitions .. only one is needed , the other two may be done away with and reused to better purpose;
remove all but 2 kernels from the sdb2 install(s), and same for the ubuntu sda install.

Let's look at what and how you are booting ... and the UUID assignments.  Are you able to boot up all of the operating systems from either of the hard drives ?
Post the output of terminal codes:
```

sudo blkid
cat /etc/fstab

```
And we can do this.[INDENT][INDENT][INDENT]just another process
[/INDENT]
[/INDENT]
[/INDENT]


Good Morning:

I am able to boot to Windows 7, 12.04 on the new drive, and 12.04 on my old drive. I tried, randomly, 2 of the selections on the list. Those bootups took me to my old drive, but there was a flash over the screen that said, "That address is already in use". However, the bootup went fine and I was able to access all drives.

Here is what sudo blkid
cat /etc/fstab

Shows:dave@dave-desktop:~$ sudo blkid
[sudo] password for dave: 
/dev/sda1: LABEL="System" UUID="BC20303E202FFDC8" TYPE="ntfs" 
/dev/sda2: LABEL="OSDisk" UUID="E01A44131A43E4DE" TYPE="ntfs" 
/dev/sda5: UUID="80d61814-fc43-4c38-b772-d32945f6b4a1" TYPE="swap" 
/dev/sda6: UUID="75e89545-dc5c-4553-907d-23269bb7b2a9" TYPE="ext4" 
/dev/sdb2: UUID="01a0c8e9-208b-446f-8194-25189c603de1" TYPE="ext4" 
/dev/sdb3: UUID="4958eedc-3298-45c0-83f3-c4e4d20e4194" TYPE="swap" 
/dev/sdb5: UUID="e35ca651-476f-4313-a744-c5021cade941" TYPE="ext4" 

dave@dave-desktop:~$ sudo blkid
[sudo] password for dave: 
/dev/sda1: LABEL="System" UUID="BC20303E202FFDC8" TYPE="ntfs" 
/dev/sda2: LABEL="OSDisk" UUID="E01A44131A43E4DE" TYPE="ntfs" 
/dev/sda5: UUID="80d61814-fc43-4c38-b772-d32945f6b4a1" TYPE="swap" 
/dev/sda6: UUID="75e89545-dc5c-4553-907d-23269bb7b2a9" TYPE="ext4" 
/dev/sdb2: UUID="01a0c8e9-208b-446f-8194-25189c603de1" TYPE="ext4" 
/dev/sdb3: UUID="4958eedc-3298-45c0-83f3-c4e4d20e4194" TYPE="swap" 
/dev/sdb5: UUID="e35ca651-476f-4313-a744-c5021cade941" TYPE="ext4" 
/dev/sdb6: UUID="6401838b-4d19-4e12-88fa-a944c9326ef9" TYPE="swap" 
dave@dave-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=75e89545-dc5c-4553-907d-23269bb7b2a9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=80d61814-fc43-4c38-b772-d32945f6b4a1 none            swap    sw              0       0
dave@dave-desktop:~$ 

Thanks for your help.

Dave

---

### Post by aviator1 on 2013-08-19
Sorry, I had the post of the requested information improperly displayed. Here is what you wanted to see, I think.......

dave@dave-desktop:~$ sudo blkid
[sudo] password for dave: 
/dev/sda1: LABEL="System" UUID="BC20303E202FFDC8" TYPE="ntfs" 
/dev/sda2: LABEL="OSDisk" UUID="E01A44131A43E4DE" TYPE="ntfs" 
/dev/sda5: UUID="80d61814-fc43-4c38-b772-d32945f6b4a1" TYPE="swap" 
/dev/sda6: UUID="75e89545-dc5c-4553-907d-23269bb7b2a9" TYPE="ext4" 
/dev/sdb2: UUID="01a0c8e9-208b-446f-8194-25189c603de1" TYPE="ext4" 
/dev/sdb3: UUID="4958eedc-3298-45c0-83f3-c4e4d20e4194" TYPE="swap" 
/dev/sdb5: UUID="e35ca651-476f-4313-a744-c5021cade941" TYPE="ext4" 
/dev/sdb6: UUID="6401838b-4d19-4e12-88fa-a944c9326ef9" TYPE="swap" 
dave@dave-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=75e89545-dc5c-4553-907d-23269bb7b2a9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=80d61814-fc43-4c38-b772-d32945f6b4a1 none            swap    sw              0       0
dave@dave-desktop:~$ sudo bilkd
[sudo] password for dave: 
sudo: bilkd: command not found
dave@dave-desktop:~$ 


dave@dave-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=75e89545-dc5c-4553-907d-23269bb7b2a9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=80d61814-fc43-4c38-b772-d32945f6b4a1 none            swap    sw              0       0
dave@dave-desktop:~$

---

### Post by Bashing-om on 2013-08-19
aviator1; Hey ..
I see nothing to keep us from proceeding ... 
!st we want hard drive sda (1st hard drive) as the the 1st boot priority .. make sure it is so !
I propose to do this in easy steps, starting with the 2nd drive sdb:
Boot up sdb and show us the outputs for sdb only at this time of:
```

sudo blkid
cat /etc/fstab
mount

```
so we know what we are, for certain, looking at ...with the end to remove all the old kernels (image & headers) ... and have only 1 swap partition active (on sda)...

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by aviator1 on 2013-08-20
> **Bashing-om said:**
> aviator1; Hey ..
I see nothing to keep us from proceeding ... 
!st we want hard drive sda (1st hard drive) as the the 1st boot priority .. make sure it is so !
I propose to do this in easy steps, starting with the 2nd drive sdb:
Boot up sdb and show us the outputs for sdb only at this time of:
```

sudo blkid
cat /etc/fstab
mount

```
so we know what we are, for certain, looking at ...with the end to remove all the old kernels (image & headers) ... and have only 1 swap partition active (on sda)...
[INDENT][INDENT]we can do this
[/INDENT]
[/INDENT]


I apologize, but I don't know how to do what you are asking. I can do each of those codes separately and post them, but do not know how to "boot up sdb" either for the 1st or 2nd drive.  Is there a way to run all these codes together?

My concept of boot up is pushing the on button and selecting the O/S.

The number 1 drive is a 256GB SSD, which has Windows 7 and 12.04 on it. My goal would be to have about 75GB for Windows 7 and about 175Gb for 12.04 (less whatever other disk requirements are) The number 2 drive is a 2 TB HDD, which will be for back up and storage.

I really appreciate your help, and can take instructions fairly well....:-) I know this can be done........Thanks again

Regards,

Dave


blkid:

dave@dave-desktop:~$ sudo blkid
[sudo] password for dave: 
/dev/sda1: LABEL="System" UUID="BC20303E202FFDC8" TYPE="ntfs" 
/dev/sda2: LABEL="OSDisk" UUID="E01A44131A43E4DE" TYPE="ntfs" 
/dev/sdb2: UUID="01a0c8e9-208b-446f-8194-25189c603de1" TYPE="ext4" 
/dev/sdb3: UUID="4958eedc-3298-45c0-83f3-c4e4d20e4194" TYPE="swap" 
/dev/sdb5: UUID="e35ca651-476f-4313-a744-c5021cade941" TYPE="ext4" 
/dev/sdb6: UUID="6401838b-4d19-4e12-88fa-a944c9326ef9" TYPE="swap" 
/dev/sda5: UUID="80d61814-fc43-4c38-b772-d32945f6b4a1" TYPE="swap" 
/dev/sda6: UUID="75e89545-dc5c-4553-907d-23269bb7b2a9" TYPE="ext4" 
dave@dave-desktop:~$ 

ca /etc/fstab:

dave@dave-desktop:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=75e89545-dc5c-4553-907d-23269bb7b2a9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=80d61814-fc43-4c38-b772-d32945f6b4a1 none            swap    sw              0       0
dave@dave-desktop:~$ 

Mount:

dave@dave-desktop:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/dave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dave)
dave@dave-desktop:~$

---

### Post by Bashing-om on 2013-08-20
aviator1; Hey ! ... We will struggle through this together.
Not a big problem.
However, the advent of the SSD (solid state device) forces a change in implementation. It is highly recommended NOT to have swap on the SSD, due to the long term effects of the write cycles. Will eventually make the default swap partition onto sdb.

Be aware that I have not to this time encountered a SSD and have no direct experience. I am aware that there are things one can/should do to optimize the performance of said SSD's.

As of now .. making sdb as the "storage drive" .. do you mean that you want to remove the current 12.04 install that is on sdb ? Or keep it as a back up for the primary operating system(s) ??
How we proceed now depends on what you want to do with sdb. If it is to be only "storage" we will not worry with cleaning up the ubuntu 12.04 install .. will use "Gparted" - ubuntu's partition editor - and make it history ... and that un-allocated space can become available for storage. Bear in mind ... for a backup OS ... we are only talking about using up 30 Gigs of that 2 TB drive... could be cheap insurance.

Choosing which drive to boot: That is a selectable option from within the BIOS settings. How one accesses those options varies greatly from one machine to another,,, just depends on what the manufacturer has set up and the bios that is installed ... Generally there is an advisory on the bios boot splash screen as to what keys activate "setup". Maybe like the "del" or the f-12" keys ...
If you installed ubuntu's on your system, you have encountered this setting in the past ... setting the CD/DVD or USB as the 1st boot priority.
Not to worry about this if sdb is to be dedicated to only a storage drive.

[INDENT][INDENT]decisions decisions decisions. what do you want to do,
[/INDENT][/INDENT]

---

### Post by aviator1 on 2013-08-20
> **Bashing-om said:**
> aviator1; Hey ! ... We will struggle through this together.
Not a big problem.
However, the advent of the SSD (solid state device) forces a change in implementation. It is highly recommended NOT to have swap on the SSD, due to the long term effects of the write cycles. Will eventually make the default swap partition onto sdb.

Be aware that I have not to this time encountered a SSD and have no direct experience. I am aware that there are things one can/should do to optimize the performance of said SSD's.

As of now .. making sdb as the "storage drive" .. do you mean that you want to remove the current 12.04 install that is on sdb ? Or keep it as a back up for the primary operating system(s) ??
How we proceed now depends on what you want to do with sdb. If it is to be only "storage" we will not worry with cleaning up the ubuntu 12.04 install .. will use "Gparted" - ubuntu's partition editor - and make it history ... and that un-allocated space can become available for storage. Bear in mind ... for a backup OS ... we are only talking about using up 30 Gigs of that 2 TB drive... could be cheap insurance.

Choosing which drive to boot: That is a selectable option from within the BIOS settings. How one accesses those options varies greatly from one machine to another,,, just depends on what the manufacturer has set up and the bios that is installed ... Generally there is an advisory on the bios boot splash screen as to what keys activate "setup". Maybe like the "del" or the f-12" keys ...
If you installed ubuntu's on your system, you have encountered this setting in the past ... setting the CD/DVD or USB as the 1st boot priority.
Not to worry about this if sdb is to be dedicated to only a storage drive.
[INDENT][INDENT]decisions decisions decisions. what do you want to do,
[/INDENT]
[/INDENT]


Bashing-om:

Thanks for your patience.

The boot sequence I found is:

PO: HL-DT-ST-BD-RE
Realtek PXE BO2 DOO
HP Office Jet 7310
P1 M4 -CT265M455D2
P4 ST2000DL003-9VT166

It appears that the first hard drive to boot is the SSD.

I would like to save all the stuff I have on the old HD. It is actually divided into 2 partitions, but I only used 1. As far as I'm concerned, I would be happy with 1 big partition on the old drive. I actually have all the old drive backed up on an external HD, so if we need to get rid of everything, I can just reload the backup. However, would I have to have 12.04 there, also?

I wrote to the Crucial folks before going with the SSD, and "they" said that I would not reach a write problem for many years based on "normal" usage. I don't know if they considered swap in their statement.

It was my thinking that the SSD would be a lot faster access than the old spinning disk, so that is why I was thinking of using the SSD as the primary operations HD for Windows 7 and 12.04, and leaving the old disk for back up and long term storage.

Would a swap partition be required on the SSD if it was the primary operating disk? With the access speed of the SSD, unless 12.04 requires one, I wouldn't think it would be necessary.

Does any of this make sense?

I really appreciate your help and patience.

Regards,

Dave

---

### Post by Bashing-om on 2013-08-20
aviator1; Sure, It all makes sense ..

SSD's have the advantage in performance, hands down !
But I say again .. from numerous advisements on this forum .. you do not want swap on the SSD.
When it comes to the swap partition there are a number of considerations;
IF you have lots of ram (say 8 GIGs) AND you will not hibernate, and you do not run real intense applications, there are those who do with out any swap at all ..for the less experienced -> not recommended by me.

The more ram you have available the less swap is required, rule of thumb for lesser ram is a tad bit more swap than ram... 

As it stands now, I do propose that we use one of the swap partitions on sdb for the sda install's swap .. simple edit to /etc/fstab file is all that will take.

If it is your desire that the sdb drive be wiped and (re-)partitioned ...You need to do some more thinking as to what all is going to access that drive ..Windows, Mac, and ubuntu use differing file system formats. What is going to be stored on that drive; movies, pictures, data and what not .. maybe a partition dedicated to each category ? If you were to format sdb as "ext4" - tried and true linux format - then Windows nor Mac can read that drive. If you format that drive as say "NTFS" for windows then you need to keep a Windows' repair disk around for whatever might happen. That is not to say one could not set up a partition to be used exclusively by ubuntu (ext4) and a partition set up to be shared between Windows/Mac/ubuntu (NTFS).
If all that you want accomplished is ubuntu removed and one of the swap partitions .. that can be done ... leaving what you have now for storage untouched, getting you the additional storage partition that was the ubuntu operating system partition. Always always back up data when making any alterations .. in particular partitioning .. never can tell what might happen .. power failure then could be a major misfortune ! But it is a piece of cake to remove a partition and set it up for re use. Care and attention to detail, because mistakes are non tolerable .. ain't no going back and doing a redo; the data can be gone gone. 5 minutes or so and it is done.-may take 2 days of study to be prepared to know what you are going to do in those few seconds -

When sdb is all squared away ... will only take synaptic a few moments to remove the old kernels and headers installed on the SSD and then "update grub". Edit "fstab" for the swap partition firstly.

It is your system ... set it up for the way you use your computer !

[INDENT]we are here to help, you say what you want to do[/INDENT]

---

### Post by aviator1 on 2013-08-21
> **Bashing-om said:**
> aviator1; Sure, It all makes sense ..

SSD's have the advantage in performance, hands down !
But I say again .. from numerous advisements on this forum .. you do not want swap on the SSD.
When it comes to the swap partition there are a number of considerations;
IF you have lots of ram (say 8 GIGs) AND you will not hibernate, and you do not run real intense applications, there are those who do with out any swap at all ..for the less experienced -> not recommended by me.

The more ram you have available the less swap is required, rule of thumb for lesser ram is a tad bit more swap than ram... 

As it stands now, I do propose that we use one of the swap partitions on sdb for the sda install's swap .. simple edit to /etc/fstab file is all that will take.

If it is your desire that the sdb drive be wiped and (re-)partitioned ...You need to do some more thinking as to what all is going to access that drive ..Windows, Mac, and ubuntu use differing file system formats. What is going to be stored on that drive; movies, pictures, data and what not .. maybe a partition dedicated to each category ? If you were to format sdb as "ext4" - tried and true linux format - then Windows nor Mac can read that drive. If you format that drive as say "NTFS" for windows then you need to keep a Windows' repair disk around for whatever might happen. That is not to say one could not set up a partition to be used exclusively by ubuntu (ext4) and a partition set up to be shared between Windows/Mac/ubuntu (NTFS).
If all that you want accomplished is ubuntu removed and one of the swap partitions .. that can be done ... leaving what you have now for storage untouched, getting you the additional storage partition that was the ubuntu operating system partition. Always always back up data when making any alterations .. in particular partitioning .. never can tell what might happen .. power failure then could be a major misfortune ! But it is a piece of cake to remove a partition and set it up for re use. Care and attention to detail, because mistakes are non tolerable .. ain't no going back and doing a redo; the data can be gone gone. 5 minutes or so and it is done.-may take 2 days of study to be prepared to know what you are going to do in those few seconds -

When sdb is all squared away ... will only take synaptic a few moments to remove the old kernels and headers installed on the SSD and then "update grub". Edit "fstab" for the swap partition firstly.

It is your system ... set it up for the way you use your computer !
[INDENT]we are here to help, you say what you want to do[/INDENT]



Bashing-om:

When I was researching the purchase of this computer, I queried here on the forums with the specifications and intended uses. I do not use much in the way of graphics, music, or large files. My use is surfing the internet, some spreadsheet and word processor use, and quite a bit of emailing, mostly just text.

The general consensus was that since I have 16GB of RAM, that a swap was not required on the SSD. I have watched the system monitor during some of my regular work, and it is usually flat lined with no swap use at all. Not even close.

The old drive for storage will be just for Linux stuff. My only real use for Windows is an online property viewer that just will not work with any kind of Linux, I also use a go to meeting website occasionally , which also requires Windows.

For the SSD, I would like to have about 75GB for Windows and 175 GB for 12.04, less any requirements on the O/S or disk. I would use it for my day to day stuff, and then back up on the old HD, and put stuff in long term storage there, as well.

I have the old HD backed up on an external HD using the back up program from 12.04.

I have no problem wiping out the old HD, as I have it all backed up on the external HD. When I originally installed 12.04 on the old disk, I made 2 partitions. I have used the 1 TB partition continuously, and have never been able to do anything with the 961GB partition. It gives me an error whenever I try to save anything to it. 

I would just as soon have 1 big partition.

If this answers your questions, let's get started.

And, thanks again for your help.

Dave

---

### Post by Bashing-om on 2013-08-21
aviator1; Hey ..

I am satisfied that you will not be utilizing swap .. with that much ram..
Proceed to (re-)partition sdb ! This tutorial is great and is what I follow .. I like the command line method. The guide is much better than I can say.
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

I personally , being overly cautious as I am, prefer to mount my storage/data partitions manually on a "on-demand" basis. You may, however, prefer to automount the drive on bootup through an entry in the /etc/fstab file.

Does not matter at this point which you do first .. re-partition or clean up (synaptic) the install on sda.
If you do not presently have synaptic installed (no longer installed by default) do in terminal:
```

sudo apt-get install synaptic

```

once you start ->

[INDENT][INDENT]over and done with, in a matter of minutes
[/INDENT][/INDENT]

---

### Post by PocketDog on 2013-08-21
My first thought for this post was ```
sudo apt-get autoremove
``` Would that not have been successful/a good idea in this instance?

---

### Post by Bashing-om on 2013-08-21
@ PocketDog;
A good practice on occasion to cleanup with "autoremove" ; however, that will not remove the old installed kernels. There are a few things the operating system will not presume. It has no way to determine if/when an old kernel might be /wanted/needed/else. Removing a kernel from the system is an operation that must be explicitly conducted at the administrator's discretion.

[INDENT][INDENT]in the process of learning
[/INDENT][/INDENT]

---

### Post by PocketDog on 2013-08-21
Wow, I always assumed autoremove removed old kernels, I never bothered to check. (I bypassed my grub menu so I don't have to select anything on boot.)  I just looked on my system and found a couple of gigabytes of old kernels!
Shows what I know...
Thanks very much, Bashing-om

---

### Post by Bashing-om on 2013-08-21
@
Hey ... this is open source at it's best ! 

We are all in this together.

[INDENT]no one knows it all but some know a lot about a little
[/INDENT]

---

### Post by VMC on 2013-08-21
Here'a script that I use when I want to remove old kernels. This is a DRY RUN only, so nothing will be altered. Its a good way of seeing what kernels will be removed:
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get --dry-run remove
```
Try that and see what kernels will or can be removed. By the way, the current running kernel will not be listed, obviously.

---

### Post by aviator1 on 2013-08-21
> **Bashing-om said:**
> aviator1; Hey ..

I am satisfied that you will not be utilizing swap .. with that much ram..
Proceed to (re-)partition sdb ! This tutorial is great and is what I follow .. I like the command line method. The guide is much better than I can say.
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

I personally , being overly cautious as I am, prefer to mount my storage/data partitions manually on a "on-demand" basis. You may, however, prefer to automount the drive on bootup through an entry in the /etc/fstab file.

Does not matter at this point which you do first .. re-partition or clean up (synaptic) the install on sda.
If you do not presently have synaptic installed (no longer installed by default) do in terminal:
```

sudo apt-get install synaptic

```


once you start ->
[INDENT][INDENT]over and done with, in a matter of minutes
[/INDENT]
[/INDENT]


I ran sudo apt-get install synaptic and it ran OK.

What next? I printed out the link and will study it tonight and in the morning.

By the way, can you explain what mount and demount means? 

Thanks for your help.

Dave

---

### Post by Bashing-om on 2013-08-22
aviator1; Good evening.

As to synaptic/removal of kernels .. my post #2 refers .. pretty straight forward .. but, anything you find confusing or do not understand completely, certainly ask for clarification.

Mount: is the means for the kernel to access other devices or file systems ( bear in mind in linux - everything is a file to the kernel ), or to show what the kernel presently has access to.
demount: do not know, that term has no meaning to me in and of it's self. -> "umount" is linux's term to UNmount a device or file system. Any device not automounted at startup must be UNmounted prior to removal or shutting the system down (file system corruption, else).
Can you give an example of what you have in mind ?

As you proceed and have questions, please ask !

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by aviator1 on 2013-08-22
> **VMC said:**
> Here'a script that I use when I want to remove old kernels. This is a DRY RUN only, so nothing will be altered. Its a good way of seeing what kernels will be removed:
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get --dry-run remove
```
Try that and see what kernels will or can be removed. By the way, the current running kernel will not be listed, obviously.

Here's what it shows:

dave@dave-desktop:~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get --dry-run remove
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.2.0-52 linux-headers-3.2.0-52-generic linux-headers-3.5.0-37
  linux-headers-3.5.0-37-generic linux-headers-generic
  linux-image-3.5.0-23-generic linux-image-3.5.0-37-generic
  linux-signed-image-3.5.0-37-generic
0 upgraded, 0 newly installed, 8 to remove and 2 not upgraded.
Remv linux-headers-generic [3.2.0.52.62]
Remv linux-headers-3.2.0-52-generic [3.2.0-52.78]
Remv linux-headers-3.2.0-52 [3.2.0-52.78]
Remv linux-headers-3.5.0-37-generic [3.5.0-37.58~precise1]
Remv linux-headers-3.5.0-37 [3.5.0-37.58~precise1]
Remv linux-image-3.5.0-23-generic [3.5.0-23.35~precise1]
Remv linux-signed-image-3.5.0-37-generic [3.5.0-37.58~precise1]
Remv linux-image-3.5.0-37-generic [3.5.0-37.58~precise1]
dave@dave-desktop:~$

---

### Post by aviator1 on 2013-08-23
> **Bashing-om said:**
> aviator1; Good evening.

As to synaptic/removal of kernels .. my post #2 refers .. pretty straight forward .. but, anything you find confusing or do not understand completely, certainly ask for clarification.

Mount: is the means for the kernel to access other devices or file systems ( bear in mind in linux - everything is a file to the kernel ), or to show what the kernel presently has access to.
demount: do not know, that term has no meaning to me in and of it's self. -> "umount" is linux's term to UNmount a device or file system. Any device not automounted at startup must be UNmounted prior to removal or shutting the system down (file system corruption, else).
Can you give an example of what you have in mind ?

As you proceed and have questions, please ask !
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


Sorry about not posting. Had to be away for a bit.

When I said I ran synaptic, I just installed it and still have the long list at boot up.

Are you ready to talk me though this?

Thanks for your help.

Dave

---

### Post by Bashing-om on 2013-08-23
aviator1; Sure, not at all a problem.

I will have to reboot into an install that I have synaptic installed on so that we can coordinate step-by-step.
Be aware one can do the kernel removals from the command line .. however, I advise synaptic's use in this instance .. much less intimidating ..
and less room for error.

[INDENT][INDENT]we will get it together
[/INDENT][/INDENT]

---

### Post by aviator1 on 2013-08-24
I heard gparted mentioned as well. Is that something we could/would use?

Thanks,

Dave

---

### Post by Bashing-om on 2013-08-24
aviator1; Hello !

I am back on .. get my attention when you are ready to remove those old kernels ..
GParted ...partition editor; wonderful tool indeed, but in these operations will not be used. It can be used if you want to practice with it ... but to set up sdb as you describe, the command line will be easier and faster; and, I think you will have a greater understanding of what you are doing to sdb using the tutorial provided.

[INDENT][INDENT]all in the process of learning
[/INDENT][/INDENT]

---

### Post by aviator1 on 2013-09-15
Hey:

Back gain. Thanks for any help.

Dave

---

### Post by Bashing-om on 2013-09-15
aviator1; Hey, still here !

Ok so we do not have a broken thread; Please relate in this thread your current situation. 
Will see what I can now do.

[INDENT][INDENT]keep'n on keep'n on
[/INDENT][/INDENT]

---

### Post by aviator1 on 2013-09-16
Thanks for your response.

Originally, my problem was/is a huge number of kernels showed at bootup. I think we were going to use synaptic to fix the issue.

However, I have a bigger problem now.

My primary drive is a 256 GB SSD with Windows 7 and Ubuntu 12.04.

I just installed the recommended nvidia drivers, and my computer will not boot to the primary as it always did. I can view and use files from the SSD using the Home folder, but apparently the system does not see the SSD during bootup. BTW, when I installed some nvidia drivers awhile back, is when the huge number of kernels appeared at bootup.

Now, when I get to the screen that gives me the choices as to where to boot to, it will only take me to my secondary drive, which is my old 2 TB HDD. Also, I get a Boot Error statement when the computer first starts, but when I hit enter, I get to the screen with the choices for bootup.

Here is where I would like to get to:

1. Use my primary drive at bootup and have about 75GB for windows and the rest for Ubuntu
2. Use my secondary drive for storage/backup It does not matter if it gets erase as I have the data backed up on an external HDD.

Any help you can offer will be greatly appreciated.

Thanks,

Dave

---

### Post by Bashing-om on 2013-09-16
aviator1; Hi !

I do not anticipate this to be a big deal; Let's deal with the booting issue first - I do not think the graphics driver can be related to what kernel gets booted . As sda is to be the primary operating system .. grub needs to be installed onto sda.
There are some older kernels still present, which get seen by Grub2 and the OS_Prober; and we will attend to that directly.

//Do we have grub correctly installed to sda and BIOS set to boot from SDA ?

Just to be sure. Grub remembers where to reinstall and we want it to reinstall to sda.

#To see what drive grub2 uses, and how things are related/uses:
```

sudo blkid
sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f
sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub
sudo grub-probe -t fs_uuid /boot/grub

```
Which will also tell us if Windows is UEFI -secure boot - enabled.

Once we know where we stand, we can proceed.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by aviator1 on 2013-09-16
I think I have things listed you asked for. It looks like it cannot find grub.

Here is what I get:

dave@dave-desktop:~$ **sudo blkid**
/dev/sda1: LABEL="System" UUID="BC20303E202FFDC8" TYPE="ntfs" 
/dev/sda2: LABEL="OSDisk" UUID="E01A44131A43E4DE" TYPE="ntfs" 
/dev/sda5: UUID="80d61814-fc43-4c38-b772-d32945f6b4a1" TYPE="swap" 
/dev/sda6: UUID="75e89545-dc5c-4553-907d-23269bb7b2a9" TYPE="ext4" 
/dev/sdb2: UUID="01a0c8e9-208b-446f-8194-25189c603de1" TYPE="ext4" 
/dev/sdb3: UUID="4958eedc-3298-45c0-83f3-c4e4d20e4194" TYPE="swap" 
/dev/sdb5: UUID="e35ca651-476f-4313-a744-c5021cade941" TYPE="ext4" 
/dev/sdb6: UUID="6401838b-4d19-4e12-88fa-a944c9326ef9" TYPE="swap" 
/dev/sdd1: LABEL="USB Disk" UUID="5953-3F14" TYPE="vfat"

dave@dave-desktop:~$ **sudo fdisk -lu**

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1cff2565

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1023999      510976    7  HPFS/NTFS/exFAT
/dev/sda2         1024000   250569727   124772864    7  HPFS/NTFS/exFAT
/dev/sda3       250570750   500117503   124773377    5  Extended
/dev/sda5       466767872   500117503    16674816   82  Linux swap / Solaris
/dev/sda6       250570752   466767871   108098560   83  Linux

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  1953514583+  ee  GPT

Disk /dev/sdd: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00026844

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          48     7831551     3915752    c  W95 FAT32 (LBA)

dave@dave-desktop:~$ **sudo parted -l**
Model: ATA M4-CT256M4SSD2 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  524MB  523MB   primary   ntfs            boot
 2      524MB   128GB  128GB   primary   ntfs
 3      128GB   256GB  128GB   extended
 6      128GB   239GB  111GB   logical   ext4
 5      239GB   256GB  17.1GB  logical   linux-swap(v1)


Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2097kB  1049kB
 2      2097kB  1021GB  1021GB  ext4
 4      1021GB  1021GB  1049kB                        bios_grub
 5      1021GB  1982GB  961GB   ext4
 6      1982GB  1991GB  9281MB  linux-swap(v1)
 3      1991GB  2000GB  9282MB  linux-swap(v1)


Model: UFD USB Flash Drive (scsi)
Disk /dev/sdd: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      24.6kB  4010MB  4010MB  primary  fat32        boot, lba

ave@dave-desktop:~$ **sudo update-grub**
sudo: update-grub: command not found
dave@dave-desktop:~$** sudo grub install /dev/s**da
sudo: grub: command not found
dave@dave-desktop:~$ **sudo blkid**
/dev/sda1: LABEL="System" UUID="BC20303E202FFDC8" TYPE="ntfs" 
/dev/sda2: LABEL="OSDisk" UUID="E01A44131A43E4DE" TYPE="ntfs" 
/dev/sda5: UUID="80d61814-fc43-4c38-b772-d32945f6b4a1" TYPE="swap" 
/dev/sda6: UUID="75e89545-dc5c-4553-907d-23269bb7b2a9" TYPE="ext4" 
/dev/sdb2: UUID="01a0c8e9-208b-446f-8194-25189c603de1" TYPE="ext4" 
/dev/sdb3: UUID="4958eedc-3298-45c0-83f3-c4e4d20e4194" TYPE="swap" 
/dev/sdb5: UUID="e35ca651-476f-4313-a744-c5021cade941" TYPE="ext4" 
/dev/sdb6: UUID="6401838b-4d19-4e12-88fa-a944c9326ef9" TYPE="swap" 
/dev/sdd1: LABEL="USB Disk" UUID="5953-3F14" TYPE="vfat" 
dave@dave-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1cff2565

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1023999      510976    7  HPFS/NTFS/exFAT
/dev/sda2         1024000   250569727   124772864    7  HPFS/NTFS/exFAT
/dev/sda3       250570750   500117503   124773377    5  Extended
/dev/sda5       466767872   500117503    16674816   82  Linux swap / Solaris
/dev/sda6       250570752   466767871   108098560   83  Linux

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  1953514583+  ee  GPT

Disk /dev/sdd: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00026844

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          48     7831551     3915752    c  W95 FAT32 (LBA)
dave@dave-desktop:~$ **sudo parted -l**
Model: ATA M4-CT256M4SSD2 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  524MB  523MB   primary   ntfs            boot
 2      524MB   128GB  128GB   primary   ntfs
 3      128GB   256GB  128GB   extended
 6      128GB   239GB  111GB   logical   ext4
 5      239GB   256GB  17.1GB  logical   linux-swap(v1)


Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  2097kB  1049kB
 2      2097kB  1021GB  1021GB  ext4
 4      1021GB  1021GB  1049kB                        bios_grub
 5      1021GB  1982GB  961GB   ext4
 6      1982GB  1991GB  9281MB  linux-swap(v1)
 3      1991GB  2000GB  9282MB  linux-swap(v1)


Model: UFD USB Flash Drive (scsi)
Disk /dev/sdd: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      24.6kB  4010MB  4010MB  primary  fat32        boot, lba


dave@dave-desktop:~$ **sudo parted /dev/sda unit s print lsblk -f**
parted: invalid option -- 'f'
Usage: parted [-hlmsv] [-a<align>] [DEVICE [COMMAND [PARAMETERS]]...]

dave@dave-desktop:~$ **sudo debconf-show grub-p**c   NOTHING HAPPENS HERE

dave@dave-desktop:~$ **sudo debconf-show grub-pc**
dave@dave-desktop:~$** sudo grub-probe -t device /boot/grub**
sudo: grub-probe: command not found

dave@dave-desktop:~$ **sudo grub-probe -t fs_uuid /boot/grub**
sudo: grub-probe: command not found

---

### Post by Bashing-om on 2013-09-16
aviator1; Wow !

Not good for the home team. Presently I do not know what to make of the null responses from "grub" commands. Strange !

Let me have a bit to look things over in depth and do some cogitating on this new development, No Grub, Yuk !

[INDENT][INDENT]I be back, soonest
[/INDENT][/INDENT]

---

### Post by aviator1 on 2013-09-16
Thanks for any help.

---

### Post by Bashing-om on 2013-09-16
aviator1; 
While I am cogitating ,,as we are looking to have to (re)install grub .. let's ensure that the package management system is stable:
```

sudo apt-get update
sudo apt-get upgrade
sudo dpkg -C

```
And yeah .. UEFI looks to be a factor (1st partition in sda drive).. I have expended a lot of effort running away from Windows and UEFI. In your case I will try and deal with it ...but, it is going to be slow and careful ... gotta keep it to where we do not harm Windows booting and still make it possible to boot ubuntu, and keep Windows playing nice with ubuntu. Possible without restoring Windows Boot code ???
Maybe the way grub is installed now, does not comprehend UEFI ?
Questions:
Do you know what hard drive you are presently booting from ? With the goal in mind to boot from sda drive;
Do you have a liveDVD -> may have to have it to restore grub where we want it installed to .. do not know for sure yet .
Do you have a Windows Disk Utility ? May have to have it when we set up ubuntu to co-exist UEFI on sda, to restore Windows' boot code.

Let's see what is:
```

apt-cache policy grub-pc

```
[INDENT]study twice, install once[/INDENT]

---

### Post by aviator1 on 2013-09-16
Here you go.

I believe I am booting from sda
I have a Windows 7 disk. It was preloaded on the machine before I installed 12.04
I have a 12.04 install cd

When I start up now, I get a "boot error", then I hit enter and it goes to the screen to choose which OS to use. There are now only about 10 choices.

If I choose the top choice, I boot to my old drive.
If I choose one of the upper kernels, I get to the screen that says no cache mode present...assuming drive cache: write through, but then it locks right there.
I can choose the bottom kernel, and it boots to where I am now.



dave@dave-desktop:~$ sudo apt-get update
[sudo] password for dave: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex    
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [417 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,031 B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [95.7 kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,343 B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [687 kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [11.5 kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [215 kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.9 kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [707 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [219 kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.0 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [2,935 B]   
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [35.5 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [5,311 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [2,378 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [36.5 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [5,206 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [2,390 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [36.3 kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5,178 B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex [72 B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex [72 B]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex [70 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex [73 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en [26.7 kB]
Fetched 2,665 kB in 10s (248 kB/s)                                             
Reading package lists... Done
dave@dave-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libx11-6 libx11-data libx11-xcb1 sessioninstaller
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 975 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libx11-data all 2:1.4.99.1-0ubuntu2.2 [172 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libx11-6 amd64 2:1.4.99.1-0ubuntu2.2 [763 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libx11-xcb1 amd64 2:1.4.99.1-0ubuntu2.2 [10.5 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main sessioninstaller all 0.20+bzr128-0ubuntu1.3 [29.5 kB]
Fetched 975 kB in 3s (281 kB/s)          
(Reading database ... 246691 files and directories currently installed.)
Preparing to replace libx11-data 2:1.4.99.1-0ubuntu2.1 (using .../libx11-data_2%3a1.4.99.1-0ubuntu2.2_all.deb) ...
Unpacking replacement libx11-data ...
Preparing to replace libx11-6 2:1.4.99.1-0ubuntu2.1 (using .../libx11-6_2%3a1.4.99.1-0ubuntu2.2_amd64.deb) ...
Unpacking replacement libx11-6 ...
Preparing to replace libx11-xcb1 2:1.4.99.1-0ubuntu2.1 (using .../libx11-xcb1_2%3a1.4.99.1-0ubuntu2.2_amd64.deb) ...
Unpacking replacement libx11-xcb1 ...
Preparing to replace sessioninstaller 0.20+bzr128-0ubuntu1.2 (using .../sessioninstaller_0.20+bzr128-0ubuntu1.3_all.deb) ...
Unpacking replacement sessioninstaller ...
Processing triggers for man-db ...
Setting up libx11-data (2:1.4.99.1-0ubuntu2.2) ...
Setting up libx11-6 (2:1.4.99.1-0ubuntu2.2) ...
Setting up libx11-xcb1 (2:1.4.99.1-0ubuntu2.2) ...
Setting up sessioninstaller (0.20+bzr128-0ubuntu1.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
dave@dave-desktop:~$ sudo dpkg -C
dave@dave-desktop:~$ sudo dpkg -c
dpkg-deb: error: --contents takes exactly one argument

Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --help for help about installing and deinstalling packages.
dave@dave-desktop:~$ apt-cache poilicy grub-pc
E: Invalid operation poilicy
dave@dave-desktop:~$

---

### Post by aviator1 on 2013-09-16
The top choice on the list at boot up is generic pae

That takes me to my old drive stuff

I can choose the bottom choice, which is 3.5.0-23 generic on dev/sda6

If this helps.

Is there any way I can copy that particular screen at boot up to show you?

Thanks

---

### Post by Bashing-om on 2013-09-16
aviator1; Yikes !

I have been busy on this.. and quite frankly .. I do not know that what you want to accomplish is possible without (RE-)installing ubuntu in UEFI mode.
Only you can know for sure. From what I gather, ubuntu must also be installed in UEFI mode 12.04.2 and higher.

The present deal: grub-pc does not speak efi. Grub is out of the equation when UEFI is in play.
So what to do !
read:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

Then: What I have observed as the recommended thing to do is Boot_Repair utility:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
consider carefully and follow through, I have seen much damage done with careless application of this utility.

Presently for my edification and instruction, I would be interested in these outputs: - from a hard drive ubuntu install -
```

[ -d /sys/firmware/efi ] && echo "Installed in EFI mode" || echo "Installed in Legacy mode"
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"

``` 

I will continue to be here to guide and assist.

[INDENT][INDENT]where there is a will there is a way, even to (RE-)installing
[/INDENT][/INDENT]

---

### Post by aviator1 on 2013-09-16
Not sure what you wanted me to do with the Legacy statements. I typed them in Terminal and here is what they show.

dave@dave-desktop:~$ [ -d /sysfirmware/efi ] && echo "Installed in EFI mode" || echo " Installed in Legacy mode"
 Installed in Legacy mode
dave@dave-desktop:~$ [ -d /sysfirmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
Legacy boot on HDD
dave@dave-desktop:~$

---

### Post by aviator1 on 2013-09-16
I have an idea.....dangerous thing........

My old 2 TB HDD is divided into 2 large partitions.  1 TB has my old stuff and 961 GB has some Unbuntu files. I had been using the 1 TB partition for everyday use, and backing up on a smaller drive while waiting for this new computer.

The second partition, I have never been able to do anything with. I get an error whenever I try to save anything there.

Since I have a 1 TB partition that is operating OK with 12.04, why don't we save my new stuff to the second partition, and I will format the SSD and reinstall Windows 7 and 12.04.

How would I copy my new Ubuntu stuff to that partition that gives me the error, or is this even a feasible plan?

Thanks very much for your help.

---

### Post by oldfred on 2013-09-16
I am seeing a BIOS  boot on sda, with Windows and one Linux install. And a BIOS boot on a gpt drive sdb, with Linux install. Which is new & which is old Ubuntu?
Depending on which MBR your boot from sda, or sdb, you may get different results.

I might just run Boot-Repair and post the link to the full BootInfo report. A lot is the same as what you have posted, but it also shows which boot loader is in which MBR. And it may let you update grub as part of its repair. I would not sue auto repair anytime you have more than one drive and install. Uncheck auto repair check update MBR and in Advanced option choose which install to put into which MBR and then change BIOS to boot from the drive.

---

### Post by aviator1 on 2013-09-16
I ran boot-repair and selected mbr repair

Here is the link [http://paste.ubuntu.com/6117078](http://paste.ubuntu.com/6117078)

I booted the top selection on the list, which takes me to my old ubuntu and here's what I get when I ran sudo apt-get


   dave@dave-desktop:~$ sudo apt-get  
 [sudo] password for dave:  
 apt 0.8.16~exp12ubuntu10.12 for i386 compiled on Jul 16 2013 18:00:58  
 Usage: apt-get [options] command  
        apt-get [options] install|remove pkg1 [pkg2 ...]  
        apt-get [options] source pkg1 [pkg2 ...]  
 

 apt-get is a simple command line interface for downloading and  
 installing packages. The most frequently used commands are update  
 and install.  
 

 Commands:  
    update - Retrieve new lists of packages  
    upgrade - Perform an upgrade  
    install - Install new packages (pkg is libc6 not libc6.deb)  
    remove - Remove packages  
    autoremove - Remove automatically all unused packages  
    purge - Remove packages and config files  
    source - Download source archives  
    build-dep - Configure build-dependencies for source packages  
    dist-upgrade - Distribution upgrade, see apt-get(8)  
    dselect-upgrade - Follow dselect selections  
    clean - Erase downloaded archive files  
    autoclean - Erase old downloaded archive files  
    check - Verify that there are no broken dependencies  
    changelog - Download and display the changelog for the given package  
    download - Download the binary package into the current directory  
 

 Options:  
   -h  This help text.  
   -q  Loggable output - no progress indicator  
   -qq No output except for errors  
   -d  Download only - do NOT install or unpack archives  
   -s  No-act. Perform ordering simulation  
   -y  Assume Yes to all queries and do not prompt  
   -f  Attempt to correct a system with broken dependencies in place  
   -m  Attempt to continue if archives are unlocatable  
   -u  Show a list of upgraded packages as well  
   -b  Build the source package after fetching it  
   -V  Show verbose version numbers  
   -c=? Read this configuration file  
   -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp  
 See the apt-get(8), sources.list(5) and apt.conf(5) manual  
 pages for more information and options. 
                        This APT has Super Cow Powers.  
 dave@dave-desktop:~$

---

### Post by aviator1 on 2013-09-16
Update:

The new drive (SSD) has the Windows 7 and 12.04  on it.

The old drive (2 TB) has 2 partitions using 12.04. One is the one I have been using for some time, and the other partition is the one that I cannot save anything to.

Thanks for your help.

Dave

---

### Post by Bashing-om on 2013-09-16
aviator1; (RE-)installing is too soon to say so - Presently I JUST DO NOT know for sure what is.

1. Windows is UEFI ,(???) nope must be a bios boot partition !
> 
dave@dave-desktop:~$ sudo parted -l
Model: ATA M4-CT256M4SSD2 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 524MB 523MB primary ntfs boot

----but------but----but-----

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1cff2565

Device Boot Start End Blocks Id System
/dev/sda1 * 2048 1023999 510976 7 HPFS/NTFS/exFAT

Something here is real screwy ! Or I am left brained again; Consider:
510976 Blocks equal 249.5 MB ---not even the reported 523 MB
whereas 523 MB equals 1071104 blocks
As this partition is not UEFI,  why does not grub then respond to commands ?

2. SDA is partitioned msdos -> then must be bios booting code
3. UEFI requires GPT partitioning !!
4 SDB is partitioned GPT

5. All this tells me we are not talking about UEFI, must be another explanation !
---------------------------------


sdb: You say with 2 partitions, "parted" shows 6 partitions. Else: you are referring to a disk that is not presently installed ?
quote]
Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number Start End Size File system Name Flags
1 1049kB 2097kB 1049kB
2 2097kB 1021GB 1021GB ext4
4 1021GB 1021GB 1049kB bios_grub
5 1021GB 1982GB 961GB ext4
6 1982GB 1991GB 9281MB linux-swap(v1)
3 1991GB 2000GB 9282MB linux-swap(v1)
[/quote]

[INDENT][INDENT]I got lots of homework yet to do[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-09-16
whoh, Am I getting behind !

@oldfred, thanks for stepping in .. please look at my last and see if you can explain the disparity I see with the sda1 partition. Maybe I am in need of education ?

---

### Post by aviator1 on 2013-09-16
Some progress has been made.

However, if I select the top selection, 3.2.0-53-generic-pae, all I get is a blinking white cursor on a black screen.

I selected one farther down and it booted to my old drive.

I think we may be getting closer.

I am back to having this:

dave@dave-desktop:~$ grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
menuentry 'Ubuntu, with Linux 3.2.0-53-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-53-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-53-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-53-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-51-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-51-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-51-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-51-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-49-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-49-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-49-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-49-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-48-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-48-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-48-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-48-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-45-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-45-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-45-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-45-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-44-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-44-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-43-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-43-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-41-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-41-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-41-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-41-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-40-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-40-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-40-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-40-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-39-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-39-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-38-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-38-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-37-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-37-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-36-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-36-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-33-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-33-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-31-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-31-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 2.6.32-42-generic' --class ubuntu --class gnu-linux --class gnu --clas
menuentry 'Ubuntu, with Linux 2.6.32-42-generic (recovery mode)' --class ubuntu --class gnu-linux --
menuentry 'Ubuntu, with Linux 2.6.32-41-generic' --class ubuntu --class gnu-linux --class gnu --clas
menuentry 'Ubuntu, with Linux 2.6.32-41-generic (recovery mode)' --class ubuntu --class gnu-linux --
menuentry 'Ubuntu, with Linux 2.6.32-40-generic' --class ubuntu --class gnu-linux --class gnu --clas
menuentry 'Ubuntu, with Linux 2.6.32-40-generic (recovery mode)' --class ubuntu --class gnu-linux --
menuentry 'Ubuntu, with Linux 2.6.32-39-generic' --class ubuntu --class gnu-linux --class gnu --clas
menuentry 'Ubuntu, with Linux 2.6.32-39-generic (recovery mode)' --class ubuntu --class gnu-linux --
menuentry 'Ubuntu, with Linux 2.6.32-38-generic' --class ubuntu --class gnu-linux --class gnu --clas
menuentry 'Ubuntu, with Linux 2.6.32-38-generic (recovery mode)' --class ubuntu --class gnu-linux --
menuentry 'Ubuntu, with Linux 2.6.32-37-generic' --class ubuntu --class gnu-linux --class gnu --clas
menuentry 'Ubuntu, with Linux 2.6.32-37-generic (recovery mode)' --class ubuntu --class gnu-linux --
menuentry 'Ubuntu, with Linux 2.6.32-36-generic' --class ubuntu --class gnu-linux --class gnu --clas
menuentry 'Ubuntu, with Linux 2.6.32-36-generic (recovery mode)' --class ubuntu --class gnu-linux --
menuentry 'Ubuntu, with Linux 2.6.32-35-generic' --class ubuntu --class gnu-linux --class gnu --clas
menuentry 'Ubuntu, with Linux 2.6.32-35-generic (recovery mode)' --class ubuntu --class gnu-linux --
menuentry 'Ubuntu, with Linux 2.6.32-34-generic' --class ubuntu --class gnu-linux --class gnu --clas
menuentry 'Ubuntu, with Linux 2.6.32-34-generic (recovery mode)' --class ubuntu --class gnu-linux --
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --clas
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --clas
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
menuentry "Ubuntu, with Linux 3.5.0-40-generic (on /dev/sda6)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.5.0-40-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.5.0-39-generic (on /dev/sda6)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.5.0-39-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.5.0-37-generic (on /dev/sda6)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.5.0-37-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.5.0-23-generic (on /dev/sda6)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.5.0-23-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --c
dave@dave-desktop:~$

---

### Post by aviator1 on 2013-09-16
The plot thickens a little.

I cannot see the following when I get to that screen. Therefore, I cannot get on the SSD, only the old HDD

menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
menuentry "Ubuntu, with Linux 3.5.0-40-generic (on /dev/sda6)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.5.0-40-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.5.0-39-generic (on /dev/sda6)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.5.0-39-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.5.0-37-generic (on /dev/sda6)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.5.0-37-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.5.0-23-generic (on /dev/sda6)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.5.0-23-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --c
dave@dave-desktop:~$

---

### Post by oldfred on 2013-09-16
I am seeing a Windows boot loader in sda, and a Windows boot partition in sda1. It is a lot larger than the usual 100MB, but is only showing the two boot files for Windows that are in a boot partition.

You still have not housecleaned all the kernels in your install in sdb2. Please houseclean those.
I like to use synaptic, but since you have upgraded, synaptic may not show the versions from the old install?

       Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kerne.:
sudo apt-get purge linux-image-3.5.0-{XX,XX,XX,XX,XX,XX}-generic
Example - yours are 3.2 and 2.6 versions:
sudo apt-get purge linux-image-3.5.0-{17,18,19,21,22,23,24}-generic

---

### Post by aviator1 on 2013-09-16
OldFred:

I really appreciate your help, however, you are speaking Greek to me.

Would I use uname-a with terminal, or synaptic.....that's how basic you will have to be with me...sorry. 

I love using Ubutnu, but I just do not know the terminology.

I ran boot-repair again and am back to the short list of choices for boot up. However, to get to my primary drive (SSD) I have to use the bottom selection.

I really appreciate the help you guys are giving, please don't give up on me because I don't understand the terms.

Thanks,

Dave

---

### Post by aviator1 on 2013-09-16
I do have synaptic, but do not have a clue what to do with it.

Dave

---

### Post by aviator1 on 2013-09-16
dave@dave-desktop:~$ uname-a
uname-a: command not found
dave@dave-desktop:~$ sudo fdisk -l
[sudo] password for dave: 

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1cff2565

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     1023999      510976    7  HPFS/NTFS/exFAT
/dev/sda2   *     1024000   250569727   124772864    7  HPFS/NTFS/exFAT
/dev/sda3       250570750   500117503   124773377    5  Extended
/dev/sda5       466767872   500117503    16674816   82  Linux swap / Solaris
/dev/sda6       250570752   466767871   108098560   83  Linux

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  1953514583+  ee  GPT

Disk /dev/sdd: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00026844

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          48     7831551     3915752    c  W95 FAT32 (LBA)
dave@dave-desktop:~$

---

### Post by Bashing-om on 2013-09-16
aviator1; Hey ..
I am here and I am now booted into 12.04 with synaptic activated.... ready to walk you through it.

first so you know what kernel NOT to remove do terminal code:
```

uname -a

```
that is a space between the command "uname" and the option "-a". I also will watch for kernels to keep.

[INDENT][INDENT]a walk in the park
[/INDENT][/INDENT]

---

### Post by aviator1 on 2013-09-16
I have synaptic fired up as well, Where does the uname -a go?

---

### Post by aviator1 on 2013-09-16
I got it...terminal

dave@dave-desktop:~$ uname -a
Linux dave-desktop 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
dave@dave-desktop:~$

---

### Post by Bashing-om on 2013-09-16
aviator1; Tattoo it on the back of your eyeball !
That is the kernel you are running on right now .. and must not remove it !
please post that output so I am aware and can make sure ..
I have a list of the kernels I "think" should be kept for you.

[INDENT][INDENT]here we go !
[/INDENT][/INDENT]

---

### Post by aviator1 on 2013-09-16
I printed it off and have it in front of me

---

### Post by Bashing-om on 2013-09-16
aviator1; That is a good thing to have ,,, I would be more comfortable if I had it too !

---

### Post by aviator1 on 2013-09-16
dave@dave-desktop:~$ uname -a
Linux dave-desktop 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
dave@dave-desktop:~$

---

### Post by aviator1 on 2013-09-16
Is that what you are looking for?

---

### Post by Bashing-om on 2013-09-16
aviator1' Got it ! not what I expected .. but we can make do ..
ok ..in synaptic you see 4 panes ... in the lower left pane is a list starting with:
sections 
status 
origin
ect

select the option "status".

---

### Post by aviator1 on 2013-09-16
Status is selected

---

### Post by Bashing-om on 2013-09-16
in the pane above it select "installed" and
below "Quick filter" is a text input box - to the left of the search tool.
in that text box type linux-image

---

### Post by aviator1 on 2013-09-16
Done

---

### Post by Bashing-om on 2013-09-16
Ok, you see a long list in the upper right pane ... right click -one at a time- all entries containing linux-image<some_version_number>-generic.
do not select version numbers: 
3.2.0-53
3.2.0-40
3.5.0-39
3.5.0-23
and select from the right click menu "mark for complete removal"

---

### Post by Bashing-om on 2013-09-16
mind you I am not seeing your screen ... if in doubt pleas ask prior to removal:

Oh!!! I left off 3.2.0-51
3.5.0-40

!!!!!!!

---

### Post by aviator1 on 2013-09-16
There were only 2 to check,,,done

---

### Post by aviator1 on 2013-09-16
Wait...which version...installed or latest version should I be looking at?

---

### Post by aviator1 on 2013-09-16
I should be looking under Package shouldn't I......

---

### Post by Bashing-om on 2013-09-16
That do surprise me ... looks as if we are going to have to find a means to boot into the sdb install and repeat this proceedure.

ok .. there are two from the 12.04 install to be removed,
If you are sure that none of the amened kernels NOT to be removed are checked for removal .. at this time 
hit apply in the top tool bar,
verify once more what you are removing in the pop up "apply following changes"
and hit the final no return gone bye bye "apply" button.

---

### Post by aviator1 on 2013-09-16
They were both -37's and they are gone

---

### Post by Bashing-om on 2013-09-16
Continuing on ! in that "quick filter box" type linux-headers 
repeat the procedure ... ask when there is a doubt.

---

### Post by aviator1 on 2013-09-16
May be a stupid questions...but I an on my need drive sda....would that make a difference for synaptic.

I can reboot to the sdb if needed.

---

### Post by aviator1 on 2013-09-16
linux-headers in the box

---

### Post by Bashing-om on 2013-09-16
yeah,, will repeat this procedure in the other install.
ok;
in that upper right pane is a listing containing the header files...same same as before .. right click all that you want removed, mark for complete removal,

---

### Post by aviator1 on 2013-09-16
There were 3 linux-headers to remove. Both were -52's

---

### Post by aviator1 on 2013-09-16
Oops...only 2 linux-hearders...both were -52's

---

### Post by Bashing-om on 2013-09-16
I did not anticipate 52's .. so long as you have kept the current kernel you are runniug on as well as one other old one we are all right.
ok
apply from the tool bar and in the pop up summary window make them gone gone by hitting "apply"

once that is done .. go back to the terminal .. and issue the terminal command:
```

sudo update-grub

```
to update all of grub's configuration files.

---

### Post by aviator1 on 2013-09-16
This is what we got......

dave@dave-desktop:~$ sudo update-grub
[sudo] password for dave: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-40-generic
Found initrd image: /boot/initrd.img-3.5.0-40-generic
Found linux image: /boot/vmlinuz-3.5.0-39-generic
Found initrd image: /boot/initrd.img-3.5.0-39-generic
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Ubuntu 12.04.3 LTS (12.04) on /dev/sdb2
Found Ubuntu 10.04.2 LTS (10.04) on /dev/sdb5
done
dave@dave-desktop:~$ ^C
dave@dave-desktop:~$

---

### Post by Bashing-om on 2013-09-16
good enough for the time being ... the -23 version we can deal with at a later time ...

ok now to deal with 12.04 (sdb2) AND 10.04 (sdb5)on sdb ..

boot into either of them at this time .. and fire up synaptic ( may have to download it once more in the 12.04 install) and repeat again the procedure !

practice makes perfect

---

### Post by aviator1 on 2013-09-16
Be back after the boot....

---

### Post by aviator1 on 2013-09-16
OK, I'm back up using the old drive.....sdb??? boot up was normal...sysnaptic is updated an running

---

### Post by Bashing-om on 2013-09-16
ok, what series of versions are you seeing in synaptic ?

---

### Post by aviator1 on 2013-09-16
Using linux-image in the box:

Under package:

They run from 2.6.32-42 up to 3.2.0-51

Lots of -XX's in between

---

### Post by aviator1 on 2013-09-16
There are no 3.5's just 2.6's and 3.2's

---

### Post by Bashing-om on 2013-09-16
you are in the 12.04 install ... in terminal once more run 
```

uname -r

```
r for brevity .. all we are interested in is the version ... keep it ! and 2 of the highest versions .. all else can be removed .

---

### Post by aviator1 on 2013-09-16
Already thought of that....I'm learning....

   da[SIZE=5]ve@dave-desktop:~$ uname -a [/SIZE]

 [SIZE=5]Linux dave-desktop 3.2.0-53-generic-pae #81-Ubuntu SMP Thu Aug 22 21:23:47 UTC 2013 i686 athlon i386 GNU/Linux [/SIZE]
 [SIZE=5]dave@dave-desktop:~$[/SIZE]

---

### Post by aviator1 on 2013-09-16
Sorry about the large print. I had enlarged for ptinting

---

### Post by Bashing-om on 2013-09-16
this one may take ya a bit ... standing by !

---

### Post by aviator1 on 2013-09-16
The uname -r is dave@dave-desktop:~$ uname -r
3.2.0-53-generic-pae
dave@dave-desktop:~$ 

Should I go ahead and remove as before, leaving the ones you listed?

---

### Post by Bashing-om on 2013-09-16
Yes indeedy ... have at it ... do you need guidance ..I can and will !

---

### Post by aviator1 on 2013-09-16
It's working on the linux-image stuff now. I'll get to the linux-header next

---

### Post by Bashing-om on 2013-09-16
roger that ! // remember to "update grub" when the headers files have been removed.

---

### Post by aviator1 on 2013-09-16
Since it is getting late, do you want to get back to this tomorrow?

---

### Post by Bashing-om on 2013-09-16
That is up to you .. I am good for better than an hour yet ...I want to hang with you .. and make sure you do a final update on the sda install after doing the sdb 10.4 .

---

### Post by aviator1 on 2013-09-16
I'm good. The status bar is about 50% for this run. Some move a little faster that others.

---

### Post by Bashing-om on 2013-09-16
mean while it is churning away .. dpkg doing it's thing...
Kinda look'n forward to seeing why the grub commands are not functioning ... my theory of UEFI related does not hold up. As UEFI is NOT in the picture !
But that will wait for a fresh mind tomorrow.

---

### Post by aviator1 on 2013-09-16
Working on the headers now

---

### Post by aviator1 on 2013-09-16
I had 1 boo-boo....I removed a -40 from the image part.....I caiught it as it was progressing.....flogging at dawn.......

---

### Post by aviator1 on 2013-09-16
OK, we are done on the image and header work.

My only screw up was that -40 in images...will that hurt us?

---

### Post by Bashing-om on 2013-09-17
Hey .. I had not thought to advise you .. you may select all of them to be removed ..and apply ---will remove the kernels in parallel !

one at a time though may be the safer approach .Makes one think about what they are doing.

---

### Post by aviator1 on 2013-09-17
What's next?

---

### Post by oldfred on 2013-09-17
I would make sure you have a current kernel installed.

Lines or text after # are comment. Copy and paste the lines one at a time, to update and make sure at least most current kernel is installed.

 #houseclean
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade
# fix Broken packages -f 
sudo apt-get -f install
sudo dpkg --configure -a

---

### Post by Bashing-om on 2013-09-17
boot into 10.04 ... synaptic is installed on 10.04 by default .. and do it again.
did you remember to run "update-grub" ?

---

### Post by aviator1 on 2013-09-17
I don't understand #houseclean or #refresh. Are those commands for terminal? also, autoclean#???

---

### Post by aviator1 on 2013-09-17
Never mind...I see it now

---

### Post by aviator1 on 2013-09-17
autoclean request gets this


dave@dave-desktop:~$ sudo apt-get autoclean
[sudo] password for dave: 
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
dave@dave-desktop:~$ ^C
dave@dave-desktop:~$

---

### Post by Bashing-om on 2013-09-17
@ oldfred; Glad you are still around ..the clean up was on my mind ..but I might have had a slip of mind with out that reminder .. before this is all done !

oldfred can I ask ya to look back at a prior post and explain the disparity I see in the size of the sda1 partition ?

---

### Post by aviator1 on 2013-09-17
Doesn't look like I can get autoclean.

How would I boot to 10.04?

---

### Post by Bashing-om on 2013-09-17
At the grub boot menu pick a 2.6 series kernel .. the highest one.
should boot to 10.04
```

apt-get autoclean

``` best work .. check that there is no typing errors.

---

### Post by aviator1 on 2013-09-17
on the way........

---

### Post by aviator1 on 2013-09-17
There are no 2.6's only  3.2's and 3.5's

---

### Post by aviator1 on 2013-09-17
dave@dave-desktop:~$ grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae' --class ubuntu --class gnu-linux --class gnu --c
menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode)' --class ubuntu --class gnu-linux
menuentry 'Ubuntu, with Linux 3.2.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class
menuentry 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --c
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
menuentry "Ubuntu, with Linux 3.5.0-40-generic (on /dev/sda6)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.5.0-40-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.5.0-39-generic (on /dev/sda6)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.5.0-39-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --c
menuentry "Ubuntu, with Linux 3.5.0-23-generic (on /dev/sda6)" --class gnu-linux --class gnu --class
menuentry "Ubuntu, with Linux 3.5.0-23-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --c
dave@dave-desktop:~$

---

### Post by aviator1 on 2013-09-17
Still cannot get autoclean

dave@dave-desktop:~$ apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
dave@dave-desktop:~$

---

### Post by Bashing-om on 2013-09-17
looks like another process has that file open .. if all else is now done to this point close all out back to the terminal and then try "apt-get autoclean" once more .. I still considering what to do to get access to 10.04. Maybe in for another learning experience ... mount that partition from the liveDVD .. and use dpkg to remove those kernels would be one way to do it .

---

### Post by aviator1 on 2013-09-17
BTW, when I get to the boot menu, there are only 2 choices that work to boot up

menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae' --class ubuntu --class gnu-linux --class gnu --c This takes me to my old drive

menuentry "Ubuntu, with Linux 3.5.0-23-generic (on /dev/sda6)" --class gnu-linux --class gnu --class This takes me to the SSD

Any other choice takes me to a black screen with a blinking white "_"

---

### Post by aviator1 on 2013-09-17
Still get the same error for autoclean

---

### Post by aviator1 on 2013-09-17
Would you be available tomorrow evening? I have a 5am get up tomorrow.

---

### Post by Bashing-om on 2013-09-17
for the lock condition what results:
```

lsof /var/cache/apt/archives/lock

```

for the non access on other kernel entries .. looks like we will have to roll up our sleeves and look at what grub is parsing from /boot.grub/grub.cfg file.

---

### Post by aviator1 on 2013-09-17
dave@dave-desktop:~$ apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
dave@dave-desktop:~$ lsof /var/cache/apt/archives/lock
dave@dave-desktop:~$ 
dave@dave-desktop:~$ 
dave@dave-desktop:~$ lsof /var/cache/apt/archives/lock
dave@dave-desktop:~$

---

### Post by Bashing-om on 2013-09-17
for the lock condition what results:
```

lsof /var/cache/apt/archives/lock

```

for the non access on other kernel entries .. looks like we will have to roll up our sleeves and look at what grub is parsing from /boot.grub/grub.cfg file.

---

### Post by aviator1 on 2013-09-17
I get no results.

dave@dave-desktop:~$ 
dave@dave-desktop:~$ 
dave@dave-desktop:~$ lsof /var/cache/apt/archives/lock
dave@dave-desktop:~$

---

### Post by aviator1 on 2013-09-17
I really need to call it a night. Can we get back to this tomorrow?

I really appreciate all you and oldfred have helped me with.

Dave

---

### Post by Bashing-om on 2013-09-17
humm .. that says no other process holds it open .. try:
```

sudo fuser -cuk /var/cache/apt/archives/lock
sudo rm -f /var/cache/apt/archives/lock

```

and maybe when we get done cleaning up the sda install and running "sudo update-grub" once more .. will put things to right with the kernels ..we will see about that.

---

### Post by aviator1 on 2013-09-17
sudo fuser -cuk /var/cache/apt/archives/lock

That locks up everything and I lose the mouse. It freezes the computer.

I'll try the second one

---

### Post by aviator1 on 2013-09-17
dave@dave-desktop:~$ sudo rm -f /var/cache/apt/archives/lock
[sudo] password for dave: 
dave@dave-desktop:~$ 



No response

---

### Post by Bashing-om on 2013-09-17
no response is a good thing .. means the system did what it was told to do and no back talk !
Does autoclean now run ?

---

### Post by aviator1 on 2013-09-17
I really appreciate your help, but I have to quit for tonight.

Dave

---

### Post by aviator1 on 2013-09-17
Got it

dave@dave-desktop:~$ apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
dave@dave-desktop:~$ sudo apt-get autoclean
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del linux-image-generic-lts-quantal 3.5.0.39.45 [2,390 B]
Del linux-generic-lts-quantal 3.5.0.39.45 [1,744 B]
Del linux-headers-generic-lts-quantal 3.5.0.37.43 [2,390 B]
Del jockey-gtk 0.9.7-0ubuntu7.9 [9,116 B]
Del jockey-common 0.9.7-0ubuntu7.9 [129 kB]
Del linux-headers-generic 3.2.0.51.61 [2,338 B]
Del linux-signed-generic-lts-quantal 3.5.0.37.43 [1,766 B]
Del linux-signed-image-generic-lts-quantal 3.5.0.37.43 [2,434 B]
Del linux-signed-image-generic-lts-quantal 3.5.0.39.45 [2,416 B]
Del linux-libc-dev 3.2.0-51.77 [859 kB]
Del linux-headers-generic 3.2.0.52.62 [2,340 B]
Del linux-signed-generic-lts-quantal 3.5.0.39.45 [1,760 B]
Del linux-generic-lts-quantal 3.5.0.37.43 [1,744 B]
Del flashplugin-installer 11.2.202.297ubuntu0.12.04.1 [6,944 B]
Del linux-image-generic-lts-quantal 3.5.0.37.43 [2,380 B]
Del linux-libc-dev 3.2.0-52.78 [855 kB]
Del linux-headers-generic-lts-quantal 3.5.0.39.45 [2,380 B]
dave@dave-desktop:~$

---

### Post by aviator1 on 2013-09-17
dave@dave-desktop:~$ apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
dave@dave-desktop:~$ sudo apt-get autoclean
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del linux-image-generic-lts-quantal 3.5.0.39.45 [2,390 B]
Del linux-generic-lts-quantal 3.5.0.39.45 [1,744 B]
Del linux-headers-generic-lts-quantal 3.5.0.37.43 [2,390 B]
Del jockey-gtk 0.9.7-0ubuntu7.9 [9,116 B]
Del jockey-common 0.9.7-0ubuntu7.9 [129 kB]
Del linux-headers-generic 3.2.0.51.61 [2,338 B]
Del linux-signed-generic-lts-quantal 3.5.0.37.43 [1,766 B]
Del linux-signed-image-generic-lts-quantal 3.5.0.37.43 [2,434 B]
Del linux-signed-image-generic-lts-quantal 3.5.0.39.45 [2,416 B]
Del linux-libc-dev 3.2.0-51.77 [859 kB]
Del linux-headers-generic 3.2.0.52.62 [2,340 B]
Del linux-signed-generic-lts-quantal 3.5.0.39.45 [1,760 B]
Del linux-generic-lts-quantal 3.5.0.37.43 [1,744 B]
Del flashplugin-installer 11.2.202.297ubuntu0.12.04.1 [6,944 B]
Del linux-image-generic-lts-quantal 3.5.0.37.43 [2,380 B]
Del linux-libc-dev 3.2.0-52.78 [855 kB]
Del linux-headers-generic-lts-quantal 3.5.0.39.45 [2,380 B]
dave@dave-desktop:~$ 
dave@dave-desktop:~$ sudo apt-get clean
dave@dave-desktop:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                     
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [417 kB]       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                  
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,031 B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [95.7 kB]  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,343 B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [687 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [11.5 kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [215 kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.9 kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [707 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [219 kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.0 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [2,935 B]   
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [35.5 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [5,311 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [2,378 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [36.5 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [5,206 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [2,390 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [36.3 kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5,178 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Fetched 2,638 kB in 8s (304 kB/s)                                              
Reading package lists... Done
dave@dave-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@dave-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@dave-desktop:~$ sudo apt-get-f install
sudo: apt-get-f: command not found
dave@dave-desktop:~$ sudo apt-get-f install
sudo: apt-get-f: command not found
dave@dave-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@dave-desktop:~$ sudo dpkg --configure -a 
dave@dave-desktop:~$ sudo dpkg --configure -a 
dave@dave-desktop:~$ sudo dpkg --configure -a 
dave@dave-desktop:~$

---

### Post by aviator1 on 2013-09-17
The last one gets no response dave@dave-desktop:~$ apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
dave@dave-desktop:~$ sudo apt-get autoclean
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del linux-image-generic-lts-quantal 3.5.0.39.45 [2,390 B]
Del linux-generic-lts-quantal 3.5.0.39.45 [1,744 B]
Del linux-headers-generic-lts-quantal 3.5.0.37.43 [2,390 B]
Del jockey-gtk 0.9.7-0ubuntu7.9 [9,116 B]
Del jockey-common 0.9.7-0ubuntu7.9 [129 kB]
Del linux-headers-generic 3.2.0.51.61 [2,338 B]
Del linux-signed-generic-lts-quantal 3.5.0.37.43 [1,766 B]
Del linux-signed-image-generic-lts-quantal 3.5.0.37.43 [2,434 B]
Del linux-signed-image-generic-lts-quantal 3.5.0.39.45 [2,416 B]
Del linux-libc-dev 3.2.0-51.77 [859 kB]
Del linux-headers-generic 3.2.0.52.62 [2,340 B]
Del linux-signed-generic-lts-quantal 3.5.0.39.45 [1,760 B]
Del linux-generic-lts-quantal 3.5.0.37.43 [1,744 B]
Del flashplugin-installer 11.2.202.297ubuntu0.12.04.1 [6,944 B]
Del linux-image-generic-lts-quantal 3.5.0.37.43 [2,380 B]
Del linux-libc-dev 3.2.0-52.78 [855 kB]
Del linux-headers-generic-lts-quantal 3.5.0.39.45 [2,380 B]
dave@dave-desktop:~$ 
dave@dave-desktop:~$ sudo apt-get clean
dave@dave-desktop:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                     
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [417 kB]       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                  
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,031 B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [95.7 kB]  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,343 B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [687 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [11.5 kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [215 kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.9 kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [707 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [219 kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.0 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [2,935 B]   
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [35.5 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [5,311 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [2,378 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [36.5 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [5,206 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [2,390 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [36.3 kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5,178 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Fetched 2,638 kB in 8s (304 kB/s)                                              
Reading package lists... Done
dave@dave-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@dave-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@dave-desktop:~$ sudo apt-get-f install
sudo: apt-get-f: command not found
dave@dave-desktop:~$ sudo apt-get-f install
sudo: apt-get-f: command not found
dave@dave-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@dave-desktop:~$ sudo dpkg --configure -a 
dave@dave-desktop:~$ sudo dpkg --configure -a 
**dave@dave-desktop:~$ sudo dpkg --configure -a **
dave@dave-desktop:~$

---

### Post by aviator1 on 2013-09-17
I really. really appreciate your help, but we will not finish this tonight.....too much left to do.

Can we get back online Tuesday evening?

---

### Post by Bashing-om on 2013-09-17
I too am pretty well done in .. before ya quit for the night .. save our present status ... by updating grub from the primary sda install ..
And while it is on my mind .. as sda is the primary hard drive .. sda is set for the 1st hard drive boot priority in bios, is it not ?

---

### Post by aviator1 on 2013-09-17
I have done a grub update.

The sda was set to primary. That is where it booted until all this occured. 

I will check the bios in the morning.

---

### Post by Bashing-om on 2013-09-17
Yeh .. I will meet ya here tomorrow eve .. do not foresee a difficulty with that.

---

### Post by aviator1 on 2013-09-17
Thanks very much for your help tonight. I have enjoyed the challenge.

I have a real early day in a few hours.

I'll check in with you tomorrow.

Kind Regards,

Dave

---

### Post by oldfred on 2013-09-17
@Bashing-om
I now see the issue you saw on sda1 size. But fdisk must have recently changed, I have just not noticed either. It used to show the sectors with fdisk -lu, but now shows blocks which are not the sectors. It is then showing the same info as parted -l even though the detail is still start & end in sectors.

---

