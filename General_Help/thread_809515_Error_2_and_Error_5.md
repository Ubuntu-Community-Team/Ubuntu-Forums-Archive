---
title: "Error 2 and Error 5"
date: 2008-05-27
forum: General Help
---

### Post by London_Red on 2008-05-27
Hi all, im new to this forum, not sure if this is the right place to post. I recently bought myself a new laptop and i now have a computer sitting at home doing nothing. My girlfriend sister's computer broke and her two young kids are now nagging her to get a new one so i decide to format the PC and give them that. So i format and realise i havent got my XP discs anymore. Fantastic!! Next i heard about Ubuntu from a mate so i gave it a go and all seemed to work fine. Installation when through and i sat praying it would work.

No luck.

I have had two different errors when trying to load up after installation. GRUB Loading Stage1.5 GRUB loading, please wait... Error 2 and now i get Error 5.

Im usually ok with computers but i asked someone to help but he said a whole mess of things i didnt understand. Is there anyone out there that could walk me through this step by step on how to fix it as i promised her the computer and i need to give it to her tomorrow and at the the moment i cant get the damn thing to work.

Any help would be much appreciated. Thank You.

P.S. I did a forum search and found a few things but i didnt really understand

---

### Post by logos34 on 2008-05-27
boot up the ubuntu live cd again, load the desktop.  Mount the root partition so you can access the files.  Open a terminal and type:

sudo fdisk -l

cat /media/disk/boot/grub/menu.lst

(or just use the nautilus file browser to go to /boot/grub/menu.lst)

Post it so we can look it over.

---

### Post by London_Red on 2008-05-27
> **logos34 said:**
> boot up the ubuntu live cd again, load the desktop.  Mount the root partition so you can access the files.  Open a terminal and type:

sudo fdisk -l

cat /media/disk/boot/grub/menu.lst

(or just use the nautilus file browser to go to /boot/grub/menu.lst)

Post it so we can look it over.
Right i have now loaded it using the disc. I am sitting with a crane type thing as my desktop but as i said im a bit special when it comes to lots of the other bits.

Now i have to mount the root partition which is done how?
Then how do i open the terminal.

Im not totally stupid but just new to all this kind of stuff so any help is brilliant.

---

### Post by London_Red on 2008-05-27
Ok i think i figured out how to do it. Im tryping using my laptop and doing the ubuntu stuff on my desktop so it will take me a while to type out all of the stuff because im no where near a wired internet. Actually forget that ill just use open office and use my usb stick. Gimme a sec and ill post what it said.

---

### Post by danwood76 on 2008-05-27
open up a terminal and post the output of:
```

sudo fdisk -l

```
That will list your computers partitions so we can give you a mount command.

Btw that 'crane' thing is a heron ;)

---

### Post by London_Red on 2008-05-27
To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 
 
ubuntu@ubuntu:~$ sudo fdisk -l 
 
Disk /dev/sda: 41.1 GB, 41110142976 bytes 
255 heads, 63 sectors/track, 4998 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x00064e27 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1         424     3405748+   7  HPFS/NTFS 
/dev/sda2             425        4998    36740655    5  Extended 
/dev/sda5             425        4810    35230513+  83  Linux 
/dev/sda6            4811        4998     1510078+  82  Linux swap / Solaris 

ubuntu@ubuntu:~$ cat /media/disk/boot/grub/menu.lst 
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
timeout		10 
 
## hiddenmenu 
# Hides the menu by default (press ESC to see the menu) 
#hiddenmenu 
 
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
# kopt=root=UUID=588366dc-08ef-4694-b8c6-26a056d420a3 ro 
 
## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 
 
## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,4) 
 
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
 
title		Ubuntu 8.04, kernel 2.6.24-16-generic 
root		(hd0,4) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=588366dc-08ef-4694-b8c6-26a056d420a3 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 
quiet 
 
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) 
root		(hd0,4) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=588366dc-08ef-4694-b8c6-26a056d420a3 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 
 
title		Ubuntu 8.04, memtest86+ 
root		(hd0,4) 
kernel		/boot/memtest86+.bin 
quiet 
 
### END DEBIAN AUTOMAGIC KERNELS LIST 
 
# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 
  
# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title		Microsoft Windows XP Professional 
root		(hd0,0) 
savedefault 
makeactive 
chainloader	+1

---

### Post by London_Red on 2008-05-27
> **danwood76 said:**
> open up a terminal and post the output of:
```

sudo fdisk -l

```
That will list your computers partitions so we can give you a mount command.

Btw that 'crane' thing is a heron ;)

You know i said i wasnt stupid well clearly i am. I should have known that as i have a marine and freshwater biology degree. Ah well. Not the proudest day for me (or my lecturers) today.

---

### Post by danwood76 on 2008-05-27
Hehe.

Well your menu.lst looks fine, the errors (2 and 5) are to do with disk geometry.
Which I find odd.

Does the WinXP boot selection work?

---

### Post by London_Red on 2008-05-27
> **danwood76 said:**
> Hehe.

Well your menu.lst looks fine, the errors (2 and 5) are to do with disk geometry.
Which I find odd.

Does the WinXP boot selection work?

I tried to boot winxp from someones disk but continually got an Error. Error Loading Operating System.

Im really confused and i feel a bit guilty because i alreaady promised the kids that they could have the computer. At the moment it seems no operating systems actually work.

---

### Post by logos34 on 2008-05-27
first thing to try is reinstalling grub.  if that doesn't work it may be your partition table that needs fixing.

in a terminal:

> [B]sudo grub

> find /boot/grub/stage1[/B]

(it should output '(hd0,4') according to fdisk)

[B]> root (hd0,4)

> setup (hd0)

> quit[/B]

ADD: check your Bios hard disk settings too.  Should be set for 'LBA' or 'Auto'

---

### Post by Gunman1982 on 2008-05-27
You formatted your xp partition so Windows is gone and no use trying to boot it apart from reinstalling completely.

Anyway I guess you are not trying to multiboot (to a non existing Win installation) so I guess the easiest way to solve this is to boot the live cd and install again. But this time when the partition manager comes up choose the "Use whole harddisk" option. I guess its the easiest way.

---

### Post by London_Red on 2008-05-27
> **logos34 said:**
> first thing to try is reinstalling grub.  if that doesn't work it may be your partition table that needs fixing.

in a terminal:

[/B]

ADD: check your Bios hard disk settings too.  Should be set for 'LBA' or 'Auto'

Ok well ill do that in the next 15 mins. How do i check the Bios part?

I have tried reinstalling the whole thing about 5 times or did you just mean reinstalling the grub part on its own?

---

### Post by London_Red on 2008-05-27
> **logos34 said:**
> first thing to try is reinstalling grub.  if that doesn't work it may be your partition table that needs fixing.

in a terminal:

[/B]

ADD: check your Bios hard disk settings too.  Should be set for 'LBA' or 'Auto'

       [ Minimal BASH-like line editing is supported.   For 
         the   first   word,  TAB  lists  possible  command 
         completions.  Anywhere else TAB lists the possible 
         completions of a device/filename. ] 
 
grub> find /boot/grub/stage1 
 (hd0,4) 
 
grub> root (hd0,4) 
 
grub> setup (hd0) 
 Checking if "/boot/grub/stage1" exists... yes 
 Checking if "/boot/grub/stage2" exists... yes 
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes 
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded. 
succeeded 
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,4)/boot/grub/stage2 
/boot/grub/menu.lst"... succeeded 
Done. 

Thats what i got. How do i check my bios to see if im running LBA or Auto?

---

### Post by logos34 on 2008-05-27
well, didn't know you reinstalled.  In that case reinstalling grub to the MBR won't help.

At startup you need to hit a key (like delete, Esc, F2 or another F key) to go into the Bios.  
[http://www.michaelstevenstech.com/bios_manufacturer.htm](http://www.michaelstevenstech.com/bios_manufacturer.htm)

---

### Post by London_Red on 2008-05-27
> **Gunman1982 said:**
> You formatted your xp partition so Windows is gone and no use trying to boot it apart from reinstalling completely.

Anyway I guess you are not trying to multiboot (to a non existing Win installation) so I guess the easiest way to solve this is to boot the live cd and install again. But this time when the partition manager comes up choose the "Use whole harddisk" option. I guess its the easiest way.

If i cant fix it any other way then thats my next port of call. If i can fix it without reinstalling then ill give that a crack if not ill reinstall and do what you said

---

### Post by London_Red on 2008-05-27
> **logos34 said:**
> well, didn't know you reinstalled.  In that case reinstalling grub to the MBR won't help.

At startup you need to hit a key (like delete, Esc, F2 or another F key) to go into the Bios.  
[http://www.michaelstevenstech.com/bios_manufacturer.htm](http://www.michaelstevenstech.com/bios_manufacturer.htm)

Ok well im trying at the moment but a friend of a friend built my computer and the only thing it has on the front is Esys and they arent on that list so im not sure how to access it. Sorry if im getting on your nerves through my ignorance.

Delete takes me to a setup screen but not the bio. F8 is the boot menu, F12 takes me to the Network boot and F10 takes me to something about bootstrap

---

### Post by London_Red on 2008-05-27
Tried so many different combinations but i just cant seem to get to the bios.:mad:


Was being an absolute idiot. Found the bios and i am now editing and seeing if i can get some joy.

---

### Post by logos34 on 2008-05-27
> **London_Red said:**
> Tried so many different combinations but i just cant seem to get to the bios.:mad:

hmm...you can try running

sudo lshw

from a terminal on the live cd

your Bios vendor will be listed at top (under '*Firmware') along with other PC info.  

On the other hand if you don't care about that NTFS partition then Gunman's suggestion sound good: reinstall on the entire disk.

But accessing the Bios is pretty basic, would be nice to know how (if only to pass on to eventual owners of the pc)

---

### Post by London_Red on 2008-05-27
> **logos34 said:**
> hmm...you can try running

sudo lshw

from a terminal on the live cd

your Bios vendor will be listed at top (under '*Firmware') along with other PC info.  

On the other hand if you don't care about that NTFS partition then Gunman's suggestion sound good: reinstall on the entire disk.

But accessing the Bios is pretty basic, would be nice to know how (if only to pass on to eventual owners of the pc)

Yeah finally got it all done. Works a treat. It seems you were right. My bios were not set to Auto. Changed that and boom im in. Im getting a small error when i try and turn it off. A black screen with some random letters but im working on that. Its pretty much fixed so thats all cool. You have been very patient and really helped me out. Thanks all who have helped.

---

### Post by logos34 on 2008-05-27
> **London_Red said:**
> Yeah finally got it all done. Works a treat. It seems you were right. My bios were not set to Auto. Changed that and boom im in. Im getting a small error when i try and turn it off. A black screen with some random letters but im working on that. Its pretty much fixed so thats all cool. You have been very patient and really helped me out. Thanks all who have helped.

no prob, my pleasure.  happy endings are nice:)

Installing a new OS sometimes can throw off the Bios disk settings--to tell the truth I've never understood how software can do that, but stuff happens...

good luck solving the other little glitch

---

### Post by danwood76 on 2008-05-28
When you say a black screen with random letters I assume this is just the standard kenrel output on shutdown.
This is supposed to be covered up by the splash screen in ubuntu.

Does it still shutdown if left alone?
There is an odd bug in hardy which might be related, heres the work around:
[http://ubuntuforums.org/showthread.php?p=4858236#post4858236](http://ubuntuforums.org/showthread.php?p=4858236#post4858236)

---

