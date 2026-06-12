---
title: "Trying to create multi &quot;Live CD&quot; USB myself"
date: 2013-06-10
forum: General Help
---

### Post by gigenieks on 2013-06-10
Hello!

IMO title is self-explanatory. I have found a few threads already on the issue with various methods suggested. While info is provided it's a bit difficult to understand (EXACTLY what I have to do).

I'll need some help along the way, because although I have used Linux time after time, my primary OS was Windows.

[#1 thread]("#1 thread")
[HowToGeek - MultiSystem]("http://www.howtogeek.com/howto/39747/how-to-boot-10-different-live-cds-from-1-usb-flash-drive/")

.....

---

### Post by greatsirkain on 2013-06-10
Would be easier to make it on windows with Sardu (gives loads of options both tool/linux/windows/antivirus etc), hasn't failed me yet where as all the different tools on linux have. He started taking direct downloads out for a lot of stuff so you have to manually download the ISOs, put them in the Sardu ISO folder and change their name to how they're listed on Sardu (it tells you what the file name should be when you hover the mouse over the button of your choice.

---

### Post by gigenieks on 2013-06-10
Manage to install MultiSystem (further in text MS) without problems.

My #1 fail:
Before using MS I did not format my USB flash drive, maybe this was a mistake (not sure).. When MS finished installing GRUB2, I just dropped Ubuntu's ISO image. It opened terminal-like window and did bunch of stuff then MS closed. When I relaunch MS I did see entry for Ubuntu. 
After that I did the same process with ArchLinux's ISO (dragged it in MS). Once again, terminal-like window > bunch of stuff. But this time it didn't close. It just added another entry for Arch.

Restart. Choose Ubuntu, got this:
[[IMG]http://i59.photobucket.com/albums/g295/gigenieks/th_IMAG0421_zps99c0ee6f.jpg[/IMG]](http://s59.photobucket.com/user/gigenieks/media/IMAG0421_zps99c0ee6f.jpg.html)

Below is screenshot of my USB flash contents:
[IMG]http://i59.photobucket.com/albums/g295/gigenieks/Multi%20Live%20CD%20USB/MS_DirectorytreeofUSBstick_zpsfc9462bb.png~original[/IMG]

What's really wierd, that Ubuntus 'ubuntu-13.04-desktop-i386' ISO didn't transform to a folder like Arch did. There is no ISO's of Arch just 1 folder with subfolders.

Well, to be sure, I tried again, first I deleted (move to trash) 'ubuntu-13.04-desktop-i386' and then added it to MS. Restart. Select Ubuntu. Same error.
Lastly, my MS window:
[[IMG]http://i59.photobucket.com/albums/g295/gigenieks/Multi%20Live%20CD%20USB/MultiSystem_009_zpsb1df92d1.png~original[/IMG]](http://s59.photobucket.com/user/gigenieks/media/Multi%20Live%20CD%20USB/MultiSystem_009_zpsb1df92d1.png.html)

How can I remove, delete both Ubuntu entries? There is no delete / remove button.
What should I try next? I'm kinda stuck.....

---

### Post by ajgreeny on 2013-06-10
But if you prefer to do it in Linux, rather than Windows, and I can't comment on the ease of using Sardu (never heard of it and don't have Windows) here are two pages of info about how to do it.  As I have stuck only with *ubuntu family OSs, I have used the method in the first of these links, and currently have a USB with 7 OSs on it, all of which boot quickly and easily.  I have not used the second link's method but it looks as if it automates the same sort of thing as the first.

My USB drive has one folder called **boot,** and in that are two folders, **grub** and **isos**.  The grub folder contains grub files including the grub.cfg file (see mine below) and the isos folder contains the .iso files, all of which I rename for ease, see list below, and that is it.  Very simple but it works!

My grub.cfg
```
menuentry "Mint 13" {
    set isofile="/boot/isos/mint-13.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}
menuentry "Lubuntu 12.04" {
    set isofile="/boot/isos/lubuntu-12.04.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}
menuentry "Xubuntu 12.04" {
    set isofile="/boot/isos/xubuntu-12.04.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}
menuentry "Ubuntu 12.04" {
    set isofile="/boot/isos/ubuntu-12.04.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}
menuentry "Bodhi 2.0" {
    set isofile="/boot/isos/bodhi-2.0.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.gz
}
menuentry "Ubuntu 12.10" {
    set isofile="/boot/isos/ubuntu-12.10.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}
menuentry "Xubuntu 12.10" {
    set isofile="/boot/isos/xubuntu-12.10.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

```
My list of OS .isos renamed for simplicity of writing the grub.cfg file; note the list matches the names in grub.cfg

bodhi-2.0.iso  
lubuntu-12.04.iso  
mint-13.iso  
ubuntu-12.04.iso  
ubuntu-12.10.iso  
xubuntu-12.04.iso  
xubuntu-12.10.iso

Your choice!  Enjoy.
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

---

### Post by gigenieks on 2013-06-10
[QUOTE=ajgreeny]
As I have stuck only with *ubuntu family OSs, I have used the method in the first of these links...
[/QUOTE]
1) I'm going to have minimum 2 distros:
[LIST]
[*]Ubuntu 13.04
[*]ArchLinux
[/LIST]
Method you provided does or doesn't support Arch?!

---

### Post by ajgreeny on 2013-06-10
I don't think it does, but to be honest, I have no idea.

---

### Post by gigenieks on 2013-06-10
I need a method / software which does. Right now I'm trying to do this with **MultiSystem** seems a good software. [Check it's amazing support!](http://translate.googleusercontent.com/translate_c?depth=1&hl=en&rurl=translate.google.lv&sl=fr&tl=en&u=http://liveusb.info/dotclear/index.php%3Fpages/os&usg=ALkJrhgduKK40dXpY22sv8QhKWgYoOsS1Q)

Unfurtunately, I don't think it has any manual in [english](http://ubuntuforums.org/showthread.php?t=2053262). :(

Update: **grub.cfg**
```

#insmod gpt
#insmod pc
#insmod gfxmenu
#
#insmod videotest
insmod tga
insmod png
insmod gfxterm
insmod lspci
#insmod vbeinfo
insmod vbe
insmod ntfs
insmod chain
insmod biosdisk
insmod font
#http://grub.enbug.org/ThemeFormat
#http://grub.gibibit.com/Theme_format#colors
#http://code.google.com/p/burg/wiki/InstallUbuntu
#http://code.google.com/p/burg/downloads/list
#http://ubuntuforums.org/showthread.php?t=1195275
#pour acces a grub2 du bootloader principal modifier dans fichier: /etc/default/grub
#GRUB_HIDDEN_TIMEOUT=10 #0 par defaut
#GRUB_HIDDEN_TIMEOUT_QUIET=false #true d'origine
#sudo update-grub
#echo -n "Press ESC to see the menu... "
#if sleep --verbose --interruptible 5 ; then
#set timeout=0
#fi
set default=0
set timeout=30
set fallback=1
search --no-floppy --fs-uuid --set=root 12E3-3D48
set root=${root}
#http://grub.enbug.org/gfxterm
if loadfont /boot/polices/unicode.pf2 ; then
set gfxmode=640x480
if terminal_output gfxterm ; then true ; else
# For backward compatibility with versions of terminal.mod that don't
# understand terminal_output
terminal gfxterm
#set gfxmode=auto
#set gfxpayload=keep
fi
fi
#set locale_dir=/boot/grub/locale
#set lang=en
#insmod gettext
if background_image /boot/splash/splash.png ; then
#text no sel/fond ecran
set color_normal=blue/black #1
#text sel/fond ecran sel
set color_highlight=green/white #1
else
set menu_color_normal=blue/black #2
set menu_color_highlight=green/white #2
set color_normal=blue/magenta #2
set color_highlight=green/white #2
fi
#set gfxpayload="1280x1024,1024x768,800x600,640x480"
#set gfxpayload=keep
#Ne supprimez pas ce marqueur! / Do not remove this marker!
#MULTISYSTEM_START
#MULTISYSTEM_MENU_DEBUT|10-06-2013-15:21:33-231159847|ubuntu-13.04-desktop-i386.iso|multisystem-ubuntu|794Mio|
menuentry "ubuntu-13.04-desktop-i386.iso" {
search --set -f "/ubuntu-13.04-desktop-i386.iso"
loopback loop "/ubuntu-13.04-desktop-i386.iso"
linux (loop)/casper/vmlinuz root=UUID=12E3-3D48 debian-installer/language=en keyboard-configuration/layoutcode=lv keyboard-configuration/variantcode=apostrophe iso-scan/filename=/ubuntu-13.04-desktop-i386.iso boot=casper file=/cdrom/preseed/ubuntu.seed noprompt quiet splash --
initrd (loop)/casper/initrd.lz
}
#MULTISYSTEM_MENU_FIN|10-06-2013-15:21:33-231159847|ubuntu-13.04-desktop-i386.iso|multisystem-ubuntu|794Mio|
#MULTISYSTEM_MENU_DEBUT|10-06-2013-15:30:05-109531975|arch1|multisystem-arch|523Mio|
menuentry "Archlinux 2011 Install 32Bits" {
linux /arch1/boot/i686/vmlinuz archisobasedir=arch1 archisolabel=PENDRIVE
initrd /arch1/boot/i686/archiso.img
}
menuentry "Archlinux 2011 Install 64Bits" {
linux /arch1/boot/x86_64/vmlinuz archisobasedir=arch1 archisolabel=PENDRIVE
initrd /arch1/boot/x86_64/archiso.img
}
#MULTISYSTEM_MENU_FIN|10-06-2013-15:30:05-109531975|arch1|multisystem-arch|523Mio|
#MULTISYSTEM_MENU_DEBUT|10-06-2013-15:57:50-529735203|ubuntu-13.04-desktop-i386.iso|multisystem-ubuntu|794Mio|
menuentry "ubuntu-13.04-desktop-i386.iso" {
search --set -f "/ubuntu-13.04-desktop-i386.iso"
loopback loop "/ubuntu-13.04-desktop-i386.iso"
linux (loop)/casper/vmlinuz root=UUID=12E3-3D48 debian-installer/language=en keyboard-configuration/layoutcode=lv keyboard-configuration/variantcode=apostrophe iso-scan/filename=/ubuntu-13.04-desktop-i386.iso boot=casper file=/cdrom/preseed/ubuntu.seed noprompt quiet splash --
initrd (loop)/casper/initrd.lz
}
#MULTISYSTEM_MENU_FIN|10-06-2013-15:57:50-529735203|ubuntu-13.04-desktop-i386.iso|multisystem-ubuntu|794Mio|
#MULTISYSTEM_MENU_DEBUT|10-06-2013-16:44:51-777386831|ubuntu-13.04-desktop-i386.iso|multisystem-ubuntu|794Mio|
menuentry "ubuntu-13.04-desktop-i386.iso" {
search --set -f "/ubuntu-13.04-desktop-i386.iso"
loopback loop "/ubuntu-13.04-desktop-i386.iso"
linux (loop)/casper/vmlinuz root=UUID=12E3-3D48 debian-installer/language=en keyboard-configuration/layoutcode=lv keyboard-configuration/variantcode=apostrophe iso-scan/filename=/ubuntu-13.04-desktop-i386.iso boot=casper file=/cdrom/preseed/ubuntu.seed noprompt quiet splash --
initrd (loop)/casper/initrd.lz
}
#MULTISYSTEM_MENU_FIN|10-06-2013-16:44:51-777386831|ubuntu-13.04-desktop-i386.iso|multisystem-ubuntu|794Mio|
#MULTISYSTEM_STOP
#Ne supprimez pas ce marqueur! / Do not remove this marker!
menuentry "______________Grub4Dos______________" {
echo
}
#http://grub4dos.sourceforge.net/
#http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial
menuentry "Grub4Dos" {
	linux /boot/grub.exe --config-file=/boot/grub/menu.lst
}
menuentry "______________Syslinux______________" {
echo
}
#solution tordue, mais qui passe partout ...
#menuentry "Syslinux" {
#search --set -f /boot/syslinux/redir.img
#	linux16 /boot/syslinux/memdisk
#	initrd16 /boot/syslinux/redir.img
#}
#http://syslinux.zytor.com
menuentry "Syslinux" {
search --set -f "/boot/syslinux/ldlinux.sys"
drivemap -s (hd0) $root
chainloader +1
}
#Autre solution pour chainer Syslinux via une copie du mbr
#dd if=/dev/sd?1 of=/media/multisystem/boot/img/syslinux.mbr bs=512 count=1
#menuentry "Syslinux" {
#search --set -f "/boot/img/syslinux.mbr"
#drivemap -s (hd0) $root
#chainloader /boot/img/syslinux.mbr
#}
menuentry "______________UTIL______________" {
echo
}
## for debugging set debug=efi
#menuentry "0-testfakebios" {
#	hexdump -s 0xc0000 (mem)
#	fakebios
#	hexdump -s 0xc0000 (mem)
## deliberate error to get wait for key
#	xxx
#}
#How to test GRUB 2 on Macbook
#http://grub.enbug.org/TestingOnMacbook
#
#http://wiki.gentoo.org/wiki/GRUB2
#
#menuentry "Windows 7 BIOS/MBR" {
#     insmod part_msdos
#     insmod ntldr
#     insmod ntfs
#     ntldr (hd0,msdos1)/bootmgr
#}
#menuentry "Windows XP BIOS/MBR" {
#     insmod part_msdos
#     insmod ntldr
#     insmod ntfs
#     ntldr (hd0,msdos1)/ntldr
#}
#
#chainer un autre grub
#menuentry "grub.cfg auf /dev/sdb1" {
#	configfile (hd1,1)/boot/grub/grub.cfg
#}
#menuentry "Chain other configfile" {
#configfile /boot/grub/grub-xxx.cfg
#}
#
#menuentry "Return default menu" {
#chainloader /boot/grub/boot.img
#}
#chainer win ou autre OS
#menuentry "Chainer UUID de la partition" {
#insmod=ntfs
#set root=(hd0,1)
#search --no-floppy --fs-uuid --set=root xxx-xxx
#	drivemap -s (hd0) $root
#	chainloader +1
#}
#http://www.plop.at/en/bootmanagerdl.html
menuentry "PLoP Boot Manager" {
	linux16 /boot/img/plpbt
}
#http://www.supergrubdisk.org/
#http://developer.berlios.de/project/showfiles.php?group_id=10921
#SG2D (Floppy, CD & USB in one)
#super_grub_disk_hybrid-1.98s1.iso
menuentry "Super Grub2 Disk" {
search --set -f /boot/img/sgdh.iso
	linux16 /boot/syslinux/memdisk
	initrd16 /boot/img/sgdh.iso
}
menuentry "Super Grub Disk" {
search --set -f /boot/img/sgdfr.img
	linux16 /boot/syslinux/memdisk
	initrd16 /boot/img/sgdfr.img
}
menuentry "Smart Boot Manager" {
search --set -f /boot/img/sbootmgr.dsk
	linux16 /boot/syslinux/memdisk
	initrd16 /boot/img/sbootmgr.dsk
}
#Site: http://boot.kernel.org/index.html
#Téléchargement: http://boot.kernel.org/gpxe_images/gpxe.lkrn
menuentry "BKO (boot.kernel.org)" {
	search --set -f /boot/img/gpxe.lkrn
	linux16 /boot/img/gpxe.lkrn
}
#http://www.memtest.org/#downiso
menuentry "memtest86+" {
	linux16 /boot/img/memtest86+.bin
}
menuentry "vbeinfo" {
	vbeinfo
read
}
menuentry "lspci" {
	lspci
read
}
menuentry "gfxpayload 640x480" {
set gfxpayload=640x480
echo gfxpayload=${gfxpayload} press enter
read
}
menuentry "gfxpayload 800x600" {
set gfxpayload=800x600
echo gfxpayload=${gfxpayload} press enter
read
}
menuentry "gfxpayload 1024x768" {
set gfxpayload=1024x768
echo gfxpayload=${gfxpayload} press enter
read
}
menuentry "gfxpayload 1280x1024" {
set gfxpayload=1280x1024
echo gfxpayload=${gfxpayload} press enter
read
}
menuentry "Reboot" {
insmod reboot
reboot
}

```

---

### Post by oldfred on 2013-06-10
I do exactly the same as ajgreeny.

I install grub2 to every flash drive, add my own grub.cfg and entries for every ISO I copy onto flash drive. Issues usually is finding correct boot parameters. All Ubuntu's are essentially the same, but I have not been able to boot server version directly only Desktops.

this shows a grub entry for Arch, but I have not booted Arch.

[https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_directly_from_GRUB](https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_directly_from_GRUB)

Booting Hard drive is the same except the drive & partition may vary where a flash drive is normally hd0 and first partition. Link on examples shows many different ISOs.
       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by gigenieks on 2013-06-10
OK it's time to read wonderful Ubuntu documentation and ask some silly questions! :D

[GRUB2/ISOBoot]("https://help.ubuntu.com/community/Grub2/ISOBoot")

> 
Ubuntu ISOs are designed to allow booting directly from the hard drive using GRUB 2 and eliminates the need for burning a CD/DVD.
In addition to Ubuntu ISOs, many other Linux distributions as well can be booted directly from an ISO file.
Another way to create a GRUB menuentry is to add it to the /etc/grub.d/40_custom file. 
It's possible to launch Kubuntu, Xubuntu etc as well many other distributions. Only requirements are GRUB2, ISO file, correct menu entry in /etc/grub.d/40_custom file. There is no need to create bootable CD/DVD or USB key?

I'm going to try create my own GRUB2 menuentry. Need a little help.
```

menuentry “Ubuntu_13.04.iso” {
set isofile=”/ubuntu-13.04-desktop-i386.iso”
loopback loop (hd[COLOR="#0000CD"]XY[/COLOR])$isofile

```
[I]"The loopback line must reflect the actual location of the ISO file. In the example, the ISO file is stored in the user's Downloads folder.
X is the drive number, starting with 0; Y is the partition number, starting with 1"[/I]
So what will be XY in my case? Do I need to go my USB keys GRUB2 to get this info? How do I do that?

Thanks!

---

### Post by oldfred on 2013-06-10
If on flash drive you can copy example from ajgreeny. Just change his path to where you saved ISO. 
His path was this: 
 set isofile="/boot/isos/lubuntu-12.04.iso", since he saved into a isos folder inside his /boot. if you have it at the top level, leave off the /boot/isos, or create a folder for the isos and save there. Note that with Linux case is important so /ISO is not /iso. I have used both in different installs and then when copying an entry wondered why it did not work.

---

### Post by gigenieks on 2013-06-10
I changed code from
```

menuentry "ubuntu-13.04-desktop-i386.iso" { 
search --set -f "/ubuntu-13.04-desktop-i386.iso" 
loopback loop "/ubuntu-13.04-desktop-i386.iso" 
linux (loop)/casper/vmlinuz root=UUID=12E3-3D48 debian-installer/language=en keyboard-configuration/layoutcode=lv keyboard-configuration/variantcode=apostrophe iso-scan/filename=/ubuntu-13.04-desktop-i386.iso boot=casper file=/cdrom/preseed/ubuntu.seed noprompt quiet splash -- 
initrd (loop)/casper/initrd.lz 
}

```
Note: This is only fragment of code, I posted full code [#7]("http://ubuntuforums.org/showthread.php?t=2153159&p=12685470#post12685470")

**to this:**
```

menuentry &#8220;Ubuntu 13.04&#8221; {
set isofile=&#8221;/ubuntu-13.04-desktop-i386.iso&#8221;
loopback loop $isofile
inux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
initrd (loop)/casper/initrd.lz
}

```
I got this when tried to start Ubuntu --->
[[IMG]http://i59.photobucket.com/albums/g295/gigenieks/Multi%20Live%20CD%20USB/th_IMAG0422_zpsdcd31721.jpg[/IMG]](http://s59.photobucket.com/user/gigenieks/media/Multi%20Live%20CD%20USB/IMAG0422_zpsdcd31721.jpg.html)

Any ideas?

---

### Post by greatsirkain on 2013-06-10
Yup you would of had to format it to fat32 if you were using Sardu.
Last time I used it, it didn't have an option for Arch but I was using an old version anyway to get hirens boot cd. You can add any live ISO on to it but if there isn't a specific option for it you would have to edit the grub cfg yourself and add the ISO to the 'extra' folder.

---

### Post by gigenieks on 2013-06-10
I'm _not using_ Sardu, I'm using **MultiSystem**.

---

### Post by sudodus on 2013-06-10
> **gigenieks said:**
> I changed code from
```

menuentry "ubuntu-13.04-desktop-i386.iso" { 
search --set -f "/ubuntu-13.04-desktop-i386.iso" 
loopback loop "/ubuntu-13.04-desktop-i386.iso" 
linux (loop)/casper/vmlinuz root=UUID=12E3-3D48 debian-installer/language=en keyboard-configuration/layoutcode=lv keyboard-configuration/variantcode=apostrophe iso-scan/filename=/ubuntu-13.04-desktop-i386.iso boot=casper file=/cdrom/preseed/ubuntu.seed noprompt quiet splash -- 
initrd (loop)/casper/initrd.lz 
}

```
Note: This is only fragment of code, I posted full code [#7]("http://ubuntuforums.org/showthread.php?t=2153159&p=12685470#post12685470")

**to this:**
```

menuentry “Ubuntu 13.04” {
set isofile=”/ubuntu-13.04-desktop-i386.iso”
loopback loop $isofile
[COLOR=#ff0000]inux[/COLOR] (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
initrd (loop)/casper/initrd.lz
}

```
I got this when tried to start Ubuntu --->
[[IMG]http://i59.photobucket.com/albums/g295/gigenieks/Multi%20Live%20CD%20USB/th_IMAG0422_zpsdcd31721.jpg[/IMG]]("http://s59.photobucket.com/user/gigenieks/media/Multi%20Live%20CD%20USB/IMAG0422_zpsdcd31721.jpg.html")

Any ideas?

I found a typo: [COLOR=#ff0000]inux[/COLOR] should be [COLOR=#008000]linux[/COLOR]

---

### Post by oldfred on 2013-06-10
I tried copying your boot stanza. But had multiple issues.

You are missing the L on the Linux line.
Your quotes are not correct. What editor did you use. You seem to have left & right " where only a standard " works. When I loaded with your quotes I got weird characters in grub. Better to use gedit. Are you in English or is your language or editor including special characters to get separate left & right quote?

---

### Post by sudodus on 2013-06-10
You have good eyes, oldfred, to find those quotes :KS

---

### Post by gigenieks on 2013-06-10
Ah missed that, sudodus. Well, it didn't change much. 2nd line in last picture changes to: 
*error: disk 'loop' not found.*

> 
Your quotes are not correct. What editor did you use. **You seem to have left & right " where only a standard " works.**

grub.cfg file was opened with gedit. Default text editor. I'm not sure I understand what you mean "Your quotes are not correct." Which quotes specifically? 
Bolded text really confuses me... Can you explain in more detail..?

---

### Post by sudodus on 2013-06-10
```
$ ascii
Usage: ascii [-dxohv] [-t] [char-alias...]
   -t = one-line output  -d = Decimal table  -o = octal table  -x = hex table
   -h = This help screen -v = version information
Prints all aliases of an ASCII character. Args may be chars, C \-escapes,
English names, ^-escapes, ASCII mnemonics, or numerics in decimal/octal/hex.

Dec Hex    Dec Hex    Dec Hex  Dec Hex  Dec Hex  Dec Hex   Dec Hex   Dec Hex  
  0 00 NUL  16 10 DLE  32 20    48 30 0  64 40 @  80 50 P   96 60 `  112 70 p
  1 01 SOH  17 11 DC1  33 21 !  49 31 1  65 41 A  81 51 Q   97 61 a  113 71 q
  2 02 STX  18 12 DC2  [COLOR=#ff0000]34 22 "[/COLOR]  50 32 2  66 42 B  82 52 R   98 62 b  114 72 r
  3 03 ETX  19 13 DC3  35 23 #  51 33 3  67 43 C  83 53 S   99 63 c  115 73 s
  4 04 EOT  20 14 DC4  36 24 $  52 34 4  68 44 D  84 54 T  100 64 d  116 74 t
  5 05 ENQ  21 15 NAK  37 25 %  53 35 5  69 45 E  85 55 U  101 65 e  117 75 u
  6 06 ACK  22 16 SYN  38 26 &  54 36 6  70 46 F  86 56 V  102 66 f  118 76 v
  7 07 BEL  23 17 ETB  39 27 '  55 37 7  71 47 G  87 57 W  103 67 g  119 77 w
  8 08 BS   24 18 CAN  40 28 (  56 38 8  72 48 H  88 58 X  104 68 h  120 78 x
  9 09 HT   25 19 EM   41 29 )  57 39 9  73 49 I  89 59 Y  105 69 i  121 79 y
 10 0A LF   26 1A SUB  42 2A *  58 3A :  74 4A J  90 5A Z  106 6A j  122 7A z
 11 0B VT   27 1B ESC  43 2B +  59 3B ;  75 4B K  91 5B [  107 6B k  123 7B {
 12 0C FF   28 1C FS   44 2C ,  60 3C <  76 4C L  92 5C \  108 6C l  124 7C |
 13 0D CR   29 1D GS   45 2D -  61 3D =  77 4D M  93 5D ]  109 6D m  125 7D }
 14 0E SO   30 1E RS   46 2E .  62 3E >  78 4E N  94 5E ^  110 6E n  126 7E ~
 15 0F SI   31 1F US   47 2F /  63 3F ?  79 4F O  95 5F _  111 6F o  127 7F DEL
```

Use the red one. You can probably copy and paste it from the table.

---

### Post by oldfred on 2013-06-10
I did not see quote issue until I tried booting with that stanza. And then grub gave really weird characters as it read them differently somehow. 

This worked but I only have 64bit so I edited that. And I have to have nomodeset to boot.

```
menuentry "Ubuntu 13.04" {
set isofile="/ubuntu-13.04-desktop-amd64.iso"
loopback loop $isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset 
initrd (loop)/casper/initrd.lz
}

```

You can copy this back and change from AMD64 to i386. Only if you have video issues may you need nomodeset. I have nVidia and cannot boot anything without nomodeset until I install nVidia drivers.

---

### Post by greatsirkain on 2013-06-10
sorry I miss-read install multisystem in your other post as what you were still trying to do - not a program. :P

---

### Post by gigenieks on 2013-06-11
I'm stuck... Let's try something different. Let's forget about my 16 GB USB flash drive with its GRUB2. Let's just try boot from Ubuntu's GRUB2 using ISO boot function.

Should be simple, right? But I can't even do that... 

[Here is separate thread, please help me do this first!?]("http://ubuntuforums.org/showthread.php?t=2153441&p=12686619#post12686619")

Then lets continue here.

---

### Post by gigenieks on 2013-06-11
I have to admit success feels good! 8-)

I finally found what was preventing my USB flash drive to boot Ubuntu.

[Here is reason #1 and #2]("http://ubuntuforums.org/showthread.php?t=2153441&p=12687008#post12687008")

Third thing which I needed to do was remove red:
```

linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt [COLOR="#B22222"]**--**[/COLOR]

```
Remove "--". No idea what it does... Well, [it works for ajgreeny]("http://ubuntuforums.org/showthread.php?t=2153159&p=12685435#post12685435"), but not for me.
Anybody has an idea why it is so??

---

### Post by VMC on 2013-06-11
> **gigenieks said:**
> I have to admit success feels good! 8-)

I finally found what was preventing my USB flash drive to boot Ubuntu.

[Here is reason #1 and #2]("http://ubuntuforums.org/showthread.php?t=2153441&p=12687008#post12687008")

Third thing which I needed to do was remove red:
```

linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt [COLOR=#B22222]**--**[/COLOR]

```
Remove "--". No idea what it does... Well, [it works for ajgreeny]("http://ubuntuforums.org/showthread.php?t=2153159&p=12685435#post12685435"), but not for me.
Anybody has an idea why it is so??

A little confused. Title says SOLVED, and first sentence here indicates the same. At any rate here's my saucy loopback that works:

I'm using an external HD to store ISO's

```
menuentry "KubuntuISO" {
    set root='(hd1,msdos1)'
    set isofile="/ISO/kde-saucy-desktop-amd64.iso"
    loopback loop (hd1,msdos1)$isofile
    linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject
    initrd (loop)/casper/initrd.lz
}
```

(note: .efi needed for saucy iso's)

---

### Post by gigenieks on 2013-06-11
Sorry, let me clarify. 

If I remove "--" iso boots. If I let them stay as they are - iso doesn't boot. 
Apparently, member ajgreeny has no problems having "--" at the end.
I'm just curious what "--" does?

---

### Post by oldfred on 2013-06-11
I noticed I remove the -- also as I always have to add nomodeset and only newer versions had that as a default in grub. So I have edited it out also. 
Not sure what function it serves.

---

### Post by C.S.Cameron on 2013-06-11
Did you remove "--" or "-- " , (--<space>).

Often when making a persistent drive I add " Persistent" after "--".

---

