---
title: "grub4dos error 32"
date: 2008-01-17
forum: General Help
---

### Post by slayer666 on 2008-01-17
Hi. I'm new to linux and I have a problem with Wubi-7.10-alpha-rev386.exe. The installation in windows vista 32bit runs smooth, but after the reboot I get unrecognized command error 32.

According to [[COLOR="Red"]this site[/COLOR]]("http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors") error 32 is : Must be authenticated
    This error is returned if you try to run a locked entry. You should enter a correct password before running such an entry.

What causes this? I cant understand it on my own.
I tried a few passwords that I thought would work but none did. ](*,)

Any help is appreciated

---

### Post by ago on 2008-01-17
Thanks for the report, I'll pass it on to tinybit and bean123, grub4dos authors

---

### Post by slayer666 on 2008-01-17
Thank you!!

---

### Post by bean123 on 2008-01-18
what's the content of your menu.lst ?

---

### Post by slayer666 on 2008-01-18
[B]I found menu.lst on 2 places.

The first 1 is found here: ubuntu\install\boot\grub\menu.lst

and here's the contents of that file:[/B]

[COLOR="Blue"]#This file is modified at runtime by bootmenu.nsh

debug off
hiddenmenu
timeout		3
default		0

title Start installer in normal mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz boot=casper find_preseed=/ubuntu/install/preseed.cfg find_iso=/ubuntu/install/ubuntu-7.10-desktop-i386.iso quiet splash ro -- automatic-ubiquity locale=sv_IT console-setup/layoutcode=it console-setup/variantcode=
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in safe graphic mode (only if you have display problems)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz xforcevesa boot=casper find_preseed=/ubuntu/install/preseed.cfg find_iso=/ubuntu/install/ubuntu-7.10-desktop-i386.iso quiet splash ro -- automatic-ubiquity locale=sv_IT console-setup/layoutcode=it console-setup/variantcode=
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer with ACPI workarounds (only if you have ACPI problems)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz acpi=off noapic nolapic quiet splash boot=casper find_preseed=/ubuntu/install/preseed.cfg find_iso=/ubuntu/install/ubuntu-7.10-desktop-i386.iso ro -- automatic-ubiquity locale=sv_IT console-setup/layoutcode=it console-setup/variantcode=
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in verbose mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debug boot=casper find_preseed=/ubuntu/install/preseed.cfg find_iso=/ubuntu/install/ubuntu-7.10-desktop-i386.iso ro -- automatic-ubiquity locale=sv_IT console-setup/layoutcode=it console-setup/variantcode=
initrd /ubuntu/install/boot/initrd.gz
boot[/COLOR]

[B]And here's the other file which is found here: ubuntu\winboot\menu.lst

And here's the contents of the second file: [/B]

[COLOR="Red"]debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 3
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt[/COLOR]

**Thank you.**  [-o<

---

### Post by bean123 on 2008-01-18
The menu seems fine, i guess it's the file system problem. please use chkdsk to fix fs inconsistency, if it still doesn't solve your problem, use fstest to get debug information.

btw, ago, i think you can use fstest to check for critical file in wubi, for example:

fstest -q comp C:\grldr

-q means no output, you can use return code to decide status:

0: ok
1: read beyond 137G limit
2: error

---

### Post by slayer666 on 2008-01-18
In which state shall I try that? in windows or when I'm stuck in grub4dos?

sorry for being me.. ;)

---

### Post by bean123 on 2008-01-18
fstest.exe is a win32 executable.you can run the following tests:

fstest info C:\
fstest inode C:\ubuntu\install\boot\grub\menu.lst
fstest comp C:\ubuntu\install\boot\grub\menu.lst
fstest inode C:\ubuntu\winboot\menu.lst
fstest comp C:\ubuntu\winboot\menu.lst

---

### Post by slayer666 on 2008-01-18
I can't run fstest in Vista.
this is what happens:

C:\>fstest info c:\
fstest is not an internal command, external command,
program or commandfile.

---

### Post by slayer666 on 2008-01-18
I found the fstest.exe in the forum.

Here's what I got:

C:\>fstest info P:\
version: 1.0
part_base: 0xC350800 (100001M)
part_leng: 0x2E035000 (376938M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x600000

C:\>fstest inode P:\ubuntu\install\boot\grub\menu.lst
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=82)
    menu.lst
  $DATA (0x80) (nr,sz=1781)
    94620472+8
Warning: reading beyond the 137G limit

C:\>fstest comp P:\ubuntu\install\boot\grub\menu.lst
File size : 1781
Comparing
Succeed
Warning: reading beyond the 137G limit

C:\>fstest inode P:\ubuntu\winboot\menu.lst
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=82)
    menu.lst
  $DATA (0x80) (nr,sz=782)
    94619416+8
Warning: reading beyond the 137G limit

C:\>fstest comp P:\ubuntu\winboot\menu.lst
File size : 782
Comparing
Succeed
Warning: reading beyond the 137G limit

---

### Post by bean123 on 2008-01-18
Inside grub4dos, use cat command to print the menu.lst, see if it's ok:

cat (hd0,N)/ubuntu/install/boot/grub/menu.lst
cat (hd0,N)/ubuntu/winboot/menu.lst

you need to figure out the value of N, there seems to be a lot of partitions in your machine.

---

### Post by ago on 2008-01-18
> **bean123 said:**
> The menu seems fine, i guess it's the file system problem. please use chkdsk to fix fs inconsistency, if it still doesn't solve your problem, use fstest to get debug information.

btw, ago, i think you can use fstest to check for critical file in wubi, for example:

fstest -q comp C:\grldr

-q means no output, you can use return code to decide status:

0: ok
1: read beyond 137G limit
2: error


Would the idea be to test the target windows drive for grub4dos compatibility before proceeding with the installation? If so it is certainly doable and a good idea. What are the implications of #1?

---

### Post by slayer666 on 2008-01-18
> **bean123 said:**
> Inside grub4dos, use cat command to print the menu.lst, see if it's ok:

cat (hd0,N)/ubuntu/install/boot/grub/menu.lst
cat (hd0,N)/ubuntu/winboot/menu.lst

you need to figure out the value of N, there seems to be a lot of partitions in your machine.

How do I do that?
I counted 14 storage units in My computer.
Is it a coinsidence that N is the 14:th letter in the alphabet?

Please laugh if I'm doing something funny. I can't help myself :)

---

### Post by bean123 on 2008-01-18
> **slayer666 said:**
> How do I do that?
I counted 14 storage units in My computer.
Is it a coinsidence that N is the 14:th letter in the alphabet?

Please laugh if I'm doing something funny. I can't help myself :)

you can use find to get the correct partition:

find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz

then

cat /ubuntu/install/boot/grub/menu.lst
cat /ubuntu/winboot/menu.lst

---

### Post by bean123 on 2008-01-18
> **ago said:**
> Would the idea be to test the target windows drive for grub4dos compatibility before proceeding with the installation? If so it is certainly doable and a good idea. What are the implications of #1?

#1 means it could cause problem in old machines, maybe you can print a warning message or so.

btw, you can also try grub2, it have an ata module that doesn't rely on bios to access hard disk.

---

### Post by ago on 2008-01-18
> **bean123 said:**
> #1 means it could cause problem in old machines, maybe you can print a warning message or so.

btw, you can also try grub2, it have an ata module that doesn't rely on bios to access hard disk.

I can only use grub2 if it is also used by default within ubuntu, and at this stage I do not think it's the case. 
Does that work on windows? Is there a grub2-4-dos?

---

### Post by bean123 on 2008-01-18
> **ago said:**
> I can only use grub2 if it is also used by default within ubuntu, and at this stage I do not think it's the case. 
Does that work on windows? Is there a grub2-4-dos?

there is a proposal to use grub2 as default boot loader for debian lenny. and you can use it to load wubi, in fact, starting grub2 from windows is very similar to grub4dos, just replace grldr and grldr.mbr with g2ldr and g2ldr.mbr, and use a different configuration file.

---

### Post by ago on 2008-01-18
> **bean123 said:**
> there is a proposal to use grub2 as default boot loader for debian lenny. and you can use it to load wubi, in fact, starting grub2 from windows is very similar to grub4dos, just replace grldr and grldr.mbr with g2ldr and g2ldr.mbr, and use a different configuration file.

My view is that diverging from default Ubuntu set-up should be avoided unless absolutely necessary (which means grub-legacy). Are the advantages of grub2 over grub4dos worth the exception in your opinion? Does grub2 support relative paths to by the way?

---

### Post by bean123 on 2008-01-18
> **ago said:**
> My view is that diverging from default Ubuntu set-up should be avoided unless absolutely necessary (which means grub-legacy). Are the advantages of grub2 over grub4dos worth the exception in your opinion? Does grub2 support relative paths to by the way?

supporting relative path is the loader's (grldr.mbr and g2ldr.mbr) job, once it's done, both grub4dos and grub2 can benefit from it.

the advantage of grub2 is direct ata access, lvm support,  etc. but i think you don't need to replace grub4dos, you can add a option that allow users to choose grub2 if they want to.

---

### Post by ago on 2008-01-18
Thanks for clarifying that bean123, I'll start playing around with that and see how it goes

---

### Post by slayer666 on 2008-01-18
Finally!!!

I managed to access the real grub4dos menu by pressing esc just after chosing ubuntu in the startmenu. I had to be really quick, 1ms too slow and I missed it.

I chose Find /ubuntu/install/boot/grub/menu.1st

And the installation started.

About the "find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.1st"

it detected (hd0,1) as the right partition to install to which makes sence as it's on the windows drive but a different partition. The drive is installed on the mainboard as no.1
The windows partition should be (hd0,0) right?

Thank you for the help, I really appreciate it!!!
:biggrin:

---

