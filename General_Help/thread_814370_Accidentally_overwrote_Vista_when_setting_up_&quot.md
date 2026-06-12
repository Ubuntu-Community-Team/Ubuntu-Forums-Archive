---
title: "Accidentally overwrote Vista when setting up &quot;dual boot&quot;; need access to documents"
date: 2008-05-31
forum: General Help
---

### Post by hockey_playa131 on 2008-05-31
I have a computer that came bundled with Vista.  I wanted something to play with so i installed Ubuntu.  Now, the issue is that when i was trying to make a partition on vista so i can install Ubuntu nothing I did worked to make the damn partition.  But my friends Tanner just installed the same Ubuntu and he couldn't make a partition either, but he's shown me HE can dual-boot between the two, and showed me how, but when i press ESC when prompted, i only get ubuntu files.  Im really mad because I can't get back to vista, and i NEEEEED TO GET BACK TO FINISH MY ENGLISH ESSAY DUE ON MONDAY!!! and i can't do a recovery on my vista drive.  PLEASE TELL ME HOW TO GET BACK TO VISTA!!!

---

### Post by Rasitiln on 2008-05-31
Obviously this wont fix your problem but can't you write it in Ubuntu and just make sure you save it in a format that is compatible with your colleges word processor (I assume word) and then upload it to your email and print it on campus? It's what I always do anyways, this works well. Occasionally I have to do some last minute formating on campus in word but it's all good.

This is assuming you can mount your vista partition.

---

### Post by nick_h on 2008-05-31
It sounds like your problem is that Vista does not appear on your grub menu.

Please post the contents of your /boot/grub/menu.lst file.

---

### Post by geo909 on 2008-05-31
STOP SHOUTING and give details. 

"I messed up my partitions and here's come bob and HE messed it up, too, but he dual boots when I can't, and how am I going to do my homework now.." 

Man, give some details! Noone will help you if you don't give more details.

---

### Post by Thanoulis on 2008-05-31
Did you install from wubi installer, or a regular installation?

---

### Post by xjgnsdof on 2008-05-31
Two words: USB backup

Seriously, though, a last resort solution would be to hook up your hard drive to another computer, boot from that computer's hard drive, and see if you can rescue your essay through the file manager. 

If that doesn't work, tell your teacher that your computer ate your homework.

---

### Post by hockey_playa131 on 2008-05-31
> **nick_h said:**
> It sounds like your problem is that Vista does not appear on your grub menu.

Please post the contents of your /boot/grub/menu.lst file.
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e85c8957-e8a4-49d1-aa78-5bbc5a797492 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=e85c8957-e8a4-49d1-aa78-5bbc5a797492 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=e85c8957-e8a4-49d1-aa78-5bbc5a797492 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e85c8957-e8a4-49d1-aa78-5bbc5a797492 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e85c8957-e8a4-49d1-aa78-5bbc5a797492 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by hockey_playa131 on 2008-05-31
> **Thanoulis said:**
> Did you install from wubi installer, or a regular installation?
disc install...

---

### Post by hockey_playa131 on 2008-05-31
> **geo909 said:**
> STOP SHOUTING and give details. 

"I messed up my partitions and here's come bob and HE messed it up, too, but he dual boots when I can't, and how am I going to do my homework now.." 

Man, give some details! Noone will help you if you don't give more details.
guy, i gave all the details i thought were relevent, what more do you want?

---

### Post by hockey_playa131 on 2008-05-31
ok, i couldn't make a partition on windows vista to install Ubuntu on.  I was told by many people that if i go through the disks instillation it would make its own partition with what ever room was left on the hard drive.  It did, but now i can't re open windows vista no matter what I do.  For a while i thought i wrote over vista and got rid of it tottally, but, i can boot windows with a recovery disk.  But the only thing i can do from that point is restore the disc to return the system to it's factory settings.  And i don't want to lose all my information.  the following is the boot/grub/menu.lst code.

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e85c8957-e8a4-49d1-aa78-5bbc5a797492 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=e85c8957-e8a4-49d1-aa78-5bbc5a797492 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=e85c8957-e8a4-49d1-aa78-5bbc5a797492 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e85c8957-e8a4-49d1-aa78-5bbc5a797492 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e85c8957-e8a4-49d1-aa78-5bbc5a797492 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

now, it doesn't let me select vista any more for a boot (well it never let me boot vista since i installed Ubuntu and yea, i need to get back into vista. so PLEASE HELP ME!

---

### Post by nick_h on 2008-05-31
There is no Vista entry in your grub configuration.

Now we need to check what partition Vista is installed on.  Please post the output of:
```
sudo fdisk -l
```

---

### Post by Rasitiln on 2008-05-31
No need to make a second thread. Spamming the forums wont get you help any faster.

---

### Post by hockey_playa131 on 2008-05-31
i don't know what you mean, what do i do with the code?

---

### Post by Rasitiln on 2008-05-31
go to Applications > accessories > terminal and type in 

```
sudo fdisk -l
```

---

### Post by hockey_playa131 on 2008-05-31
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30027   241191846   83  Linux
/dev/sda2           30028       30401     3004155    5  Extended
/dev/sda5           30028       30401     3004123+  82  Linux swap / Solaris
dylan@dylan-desktop:~$

---

### Post by nick_h on 2008-05-31
You no longer have a Windows partition.  It looks like you overwrote your Windows with Ubuntu.

Have you got any backups?

---

### Post by hockey_playa131 on 2008-05-31
no backups of what i need off of it, but i can get BACK into vista using the recovery disk but i can only re format my entire computer, and lose everything and nothign more at that point

---

### Post by Rasitiln on 2008-05-31
You could likely save time and just start writing it in open office and do as I suggested in my first post, except for mounting your windows partition obviously. I assume time is critical given your obvious stress.

---

### Post by hal8000 on 2008-05-31
sorry missed duplicate thread

---

### Post by Unix_Slayer on 2008-05-31
[**_http://www.supergrubdisk.org/_**]("http://www.supergrubdisk.org/")

It might still be there. Have you run Vista at all since you installed Ubuntu?

---

### Post by Unix_Slayer on 2008-05-31
> **hockey_playa131 said:**
> I have a computer that came bundled with Vista.  I wanted something to play with so i installed Ubuntu.  Now, the issue is that when i was trying to make a partition on vista so i can install Ubuntu nothing I did worked to make the damn partition.  But my friends Tanner just installed the same Ubuntu and he couldn't make a partition either, but he's shown me HE can dual-boot between the two, and showed me how, but when i press ESC when prompted, i only get ubuntu files.  Im really mad because I can't get back to vista, and i NEEEEED TO GET BACK TO FINISH MY ENGLISH ESSAY DUE ON MONDAY!!! and i can't do a recovery on my vista drive.  PLEASE TELL ME HOW TO GET BACK TO VISTA!!!


I know this doesn't help right now. But I tell everyone to use two hard drives. One for Vista, and one for Linux. I never let them touch except through wine.

---

### Post by jpeddicord on 2008-05-31
Threads merged. Please reply to your posts with new information, not make new threads. :)

---

### Post by dwasifar on 2008-05-31
> **hockey_playa131 said:**
> no backups of what i need off of it, but i can get BACK into vista using the recovery disk but i can only re format my entire computer, and lose everything and nothign more at that point

I'm guessing that when you say you are getting "back into Vista" what you mean is that you are booting Vista from the recovery disk, and seeing a plain-jane, generic Vista, right?  You do not see your old Vista installation when you boot that way, is that correct?

If so, then what you are seeing is the recovery screen.  It is not the same thing as your original Vista installation.  As far as I can tell from what you have written so far, the people who have told you your Vista installation is gone are correct.  You have no Vista entry in your Grub menu and no Vista partition on your drive.  From the looks of things, you wiped your hard drive when you installed Ubuntu.

There was a point during the installation where you had choices like "Resize partition and install Ubuntu in the available space" or "Guided: Use entire disk."  You had to have chosen one of those and SPECIFICALLY clicked the "Yes" button to proceed; at that point in the installation process, the default is "No."

Your best option at this point, short of professional data recovery $services$, is to reinstall Vista from the recovery disk if you really need it, and recreate your document from whatever backup you may have made - or from scratch, if you have no backup.

---

### Post by SirPerigrin on 2008-05-31
DO NOT reinstall Vista if you have ANY desire to recover the lost document!!! 

Its obvious that indeed the ubuntu install did in fact eat your vista installation. However that does not mean you need professional services or an act of god to get the data back. Testdisk and its acompanying program Photorec are great cross platform file/disc recovery tools. It is very likely that were you to run photorec with the instruction to only recover .doc files you could very easily come across your essay. Chance of recovery depends heavily upon where ubuntu wrote to the disc during install and where the file was stored on the disc by Vista. i recomend telling photorec to output to an External USB/Firewire/eSata storage device like a flash drive or Ext HDD. 

This is not a guaraunteed solution, but its a chance at getting your data back.

---

### Post by hockey_playa131 on 2008-05-31
Thanks anyway guys, I am very confident that I can get portions of my files back using a pro recovery program, so thats what I intend to do.  But for now, I'm going to use the recovery disc and re-install windows vista, then ENSURE I have a partition set up for Ubuntu and try it again.  Thanks again guys! You gave me some hope as to understanding Ubuntu and the instilation process! have a good one and i will be back later if my idea works

---

### Post by Lord Xeb on 2008-05-31
Okay, here is your problem. When you installed Ubuntu it destroyed the MBR (Master Boot Record) which allows you system to boot. Grub replaced it and now there is no boot record for Vista on Grub. 


Boot into Ubuntu and open terminal, then type the following:

```
sudo su
```

Next you want to retrieve the grub menu with: 

```
gedit /boot/grub/menu.lst
```

Go down to the bottom, and put in the following:


```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista
root		(hd0,2)
savedefault	1
makeactive
chainloader	+1
```

Once you are done. it should look like this:

## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-17-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=e85c8957-e8a4-49d1-aa78-5bbc5a797492 ro quiet splash
initrd /boot/initrd.img-2.6.24-17-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=e85c8957-e8a4-49d1-aa78-5bbc5a797492 ro single
initrd /boot/initrd.img-2.6.24-17-generic

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=e85c8957-e8a4-49d1-aa78-5bbc5a797492 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=e85c8957-e8a4-49d1-aa78-5bbc5a797492 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

# on /dev/sda3  (<--- For here, fdisk -l and look for a partition that is formated to NTFS. EX: If it says '/dev/sda5' is formated to NTFS, then you would put the partition's name here)
title		Windows Vista
root		(hd0,2) (<--- the same for here, it must be right or it won't work)
savedefault	1
makeactive
chainloader	+1
### END DEBIAN AUTOMAGIC KERNELS LIST



If you are lost, please go to terminal and type: sudo fdisk -l


Then copy and paste what it says in this tread and we will help you.




Also, the #1 rule you should always do is backup, backup, backup. When I do a project, I have 3-4 backups. One on my main HDD, the second on my external 500GB, and the thrid on a flash drive. And for extra security, I burn it to a disc.

---

### Post by Unix_Slayer on 2008-05-31
> **Lord Xeb said:**
> Also, the #1 rule you should always do is backup, backup, backup. When I do a project, I have 3-4 backups. One on my main HDD, the second on my external 500GB, and the thrid on a flash drive. And for extra security, I burn it to a disc.

I totally agree. I've always backed up three to four times a day. Be it Vista, or Ubuntu. You never know.

---

### Post by dwasifar on 2008-05-31
> **Lord Xeb said:**
> Okay, here is your problem. When you installed Ubuntu it destroyed the MBR (Master Boot Record) which allows you system to boot. Grub replaced it and now there is no boot record for Vista on Grub. 

....

# on /dev/sda3  (<--- For here, fdisk -l and look for a partition that is formated to NTFS. EX: If it says '/dev/sda5' is formated to NTFS, then you would put the partition's name here)
title		Windows Vista
root		(hd0,2) (<--- the same for here, it must be right or it won't work)
savedefault	1
makeactive
chainloader	+1
### END DEBIAN AUTOMAGIC KERNELS LIST

If you are lost, please go to terminal and type: sudo fdisk -l

Xeb, that is not his problem.  He has already posted his fdisk -l earlier in this thread, and this is it:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

Device Boot Start End Blocks Id System
/dev/sda1 * 1 30027 241191846 83 Linux
/dev/sda2 30028 30401 3004155 5 Extended
/dev/sda5 30028 30401 3004123+ 82 Linux swap / Solaris
dylan@dylan-desktop:~$
```

He has no Vista partition.  He overwrote his Vista installation.

Unless he has a backup, he's basically screwed.

---

### Post by Lord Xeb on 2008-05-31
Yeah, you are right... Well, sorry man. Unless you know how to do byte by byte recovery, your screwed. Your stuff is still on your disc, you just overwrote it with a new format and partition. It can be recovered, but it is a long, tedious process that it isn't worth the time. Or you can spend a few grand and send it in to the FBI or CIA and they recover it in a jiff.

---

### Post by Unix_Slayer on 2008-05-31
> **dwasifar said:**
> Xeb, that is not his problem.  He has already posted his fdisk -l earlier in this thread, and this is it:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

Device Boot Start End Blocks Id System
/dev/sda1 * 1 30027 241191846 83 Linux
/dev/sda2 30028 30401 3004155 5 Extended
/dev/sda5 30028 30401 3004123+ 82 Linux swap / Solaris
dylan@dylan-desktop:~$
```

He has no Vista partition.  He overwrote his Vista installation.

Unless he has a backup, he's basically screwed.


OUCH! That hurts when you say it like that.

---

### Post by Unix_Slayer on 2008-05-31
> **Lord Xeb said:**
> Yeah, you are right... Well, sorry man. Unless you know how to do byte by byte recovery, your screwed. Your stuff is still on your disc, you just overwrote it with a new format and partition. It can be recovered, but it is a long, tedious process that it isn't worth the time. Or you can spend a few grand and send it in to the FBI or CIA and they recover it in a jiff.

Or he can purchase a recovery software that will recover the partition. Acronis media builder would work.  I can't remember what they all are.

---

### Post by SirPerigrin on 2008-05-31
Does nobody read post? Photorec is FREE and OPEN SOURCE!!! And fully capable of doing what any expensive paid program can do... I can only give you a solution, its up to you to use it.

---

### Post by Unix_Slayer on 2008-05-31
This is for Lord Xeb

Pics removed.

---

### Post by Unix_Slayer on 2008-05-31
Ouch.... I ruined the thread. Funny.... all those fans are spinning. I guess my camera really works well.

---

### Post by nick_h on 2008-06-01
> **SirPerigrin said:**
> DO NOT reinstall Vista if you have ANY desire to recover the lost document!!! 

Its obvious that indeed the ubuntu install did in fact eat your vista installation. However that does not mean you need professional services or an act of god to get the data back. Testdisk and its acompanying program Photorec are great cross platform file/disc recovery tools. It is very likely that were you to run photorec with the instruction to only recover .doc files you could very easily come across your essay. Chance of recovery depends heavily upon where ubuntu wrote to the disc during install and where the file was stored on the disc by Vista. i recomend telling photorec to output to an External USB/Firewire/eSata storage device like a flash drive or Ext HDD. 

This is not a guaraunteed solution, but its a chance at getting your data back.

Yes, if you are attempting to recover data from a disk then the best thing to do is to stop using it.  Writing any data to it will reduce your chances of recovering data.

Utilities such as photorec are certainly worth a try.

---

### Post by SirPerigrin on 2008-06-01
Probobly should have put this in with my original post, here is a step by step guide to using photorec that should be pretty noob friendly.
> [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

 I highly recommend using a LiveCD to perform the recovery attempt such as the one available here
> [http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

the homepage has a case study on recovery of a .docx file you should also find very useful

---

### Post by hockey_playa131 on 2008-06-01
well folks, i did a full system recovery, and Im back to vista, WITH a 50gb partition for Ubuntu, Fully installed!!! :D so im friken happy! and what's more, i got every single last file i had before it got wiped (except for a few songs and movies i had but i can just re-rip them so it's all good) Thanks you guys for your help! Glad to know you can always depend on the kindness of stanger "nerds" lma0 but you guys are fantastic! thanks again!

---

### Post by Unix_Slayer on 2008-06-01
> **hockey_playa131 said:**
> well folks, i did a full system recovery, and Im back to vista, WITH a 50gb partition for Ubuntu, Fully installed!!! :D so im friken happy! and what's more, i got every single last file i had before it got wiped (except for a few songs and movies i had but i can just re-rip them so it's all good) Thanks you guys for your help! Glad to know you can always depend on the kindness of stanger "nerds" lma0 but you guys are fantastic! thanks again!


Congrats there Hockey_playa. May the Force Be With You... [IMG]http://planetsmilies.net/star-wars-smiley-5472.gif[/IMG]  [IMG]http://www.forumsextreme.com/imgs1/sSW_r2d2-3.gif[/IMG]

---

### Post by werries on 2008-06-01
wow. wow. wow.
mind explaining what you did? did you use photorec?
cause i read this whole thread and was convinced you were screwed.

---

### Post by SirPerigrin on 2008-06-01
Glad to hear it!!! Nothing quite so gratifying as knowing we've helped someone :)

---

### Post by Unix_Slayer on 2008-06-02
> **werries said:**
> wow. wow. wow.
mind explaining what you did? did you use photorec?
cause i read this whole thread and was convinced you were screwed.


I don't think he will tell. [IMG]http://www.tech-faq.com/emoticons/pensive/pensif_28.gif[/IMG]


Doesn't this look like the face of an honest man? [IMG]http://mysite.verizon.net/mgm_mgm/billgates.jpg[/IMG]

---

