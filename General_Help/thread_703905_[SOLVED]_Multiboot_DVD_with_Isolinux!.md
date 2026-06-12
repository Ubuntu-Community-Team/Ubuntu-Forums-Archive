---
title: "[SOLVED] Multiboot DVD with Isolinux!"
date: 2008-02-21
forum: General Help
---

### Post by jabagawee on 2008-02-21
Okay, before you start complaining of how I'm such a noob for not using the search function, I must tell you that I did. I even used Google! :O

There was that Nautopia script (went down), that mirror of the script (not good enough for me), that pcquest article (too weird sounding, dealed with Knoppix and some random cheat codes for Knoppix-based distros), etc. FInally, I decided to use CDShell. Wait a second, all the CDs I wanted to fit added up to more than 4.7GB. But if I remove the Windows XP disc...I have exactly 4.7GB! Now...I have all Linux distros! Why bother CDShell to interface with Isolinx for me when I can do pure Isolinux...? And so, I beseech the members of this lovely forum: find me an isolinux guru with too much time on his hands! Respond to me via the forum or XMPP: jabagawee on the gmail servers.

Here is the list of distros I will attempt to be using:
1) Backtrack 2 Final [COLOR="Red"]Scrapped because I won't be using it that often[/COLOR]
2) Damn Small Linux 4.2.5 [COLOR="DarkGreen"]Integrated[/COLOR]
3) Linux Mint 4.0 [COLOR="Red"]Scrapped for being too similar to Ubuntu and too hard to integrate[/COLOR]
4) Ophcrack 1.2.2 [COLOR="DarkGreen"]Integrated[/COLOR]
5) PCLinuxOS 2007 [COLOR="DarkGreen"]Integrated[/COLOR]
6) Puppy Linux 3.01 [COLOR="Red"]Scrapped for hanging at hardware detection[/COLOR]
7) Super GRUB Disk 0.9677 [COLOR="Red"]Scrapped for having functionality included in basically all of my distros[/COLOR]
8) System Rescue CD 0.4.2 [COLOR="DarkGreen"]Integrated[/COLOR]
9) Ubuntu 7.10 [COLOR="DarkGreen"]Integrated[/COLOR]
10) Xubuntu 7.10 [COLOR="Red"]Scrapped cause I already have two lightweight distros and I'm lazy[/COLOR]

Any hints? Suggestions? Do I really need Backtrack? Does DSL and Puppy on one disk seem stupid (not if one's incompatible with the computer's hardware, it isn't)? Can I eliminate Super GRUB Disk with GRUB built into Ubuntu? Should I add Kubuntu to show off KDE as an alternative to Ubuntu, or just leave the KDE exhibitions to the other distros? If someone's computer is slow enough to require Xubuntu, should I just use DSL and Puppy instead and leave Xubuntu home? Comments are welcome.

---

### Post by mrsteveman1 on 2008-02-21
Booting all the linux distros shouldnt be too hard because almost all of them use a compressed filesystem image sitting on the CD, so it should be simple to add entries to the isolinux.cfg file for each one.

To start off i would unpack the contents of each ISO file into a separate directory, then add each entry to the isolinux.cfg file. If you want a guide take a look at the isolinux.cfg file on the ubuntu CD, its a good example of how it works.

Since syslinux and isolinux share a syntax for their config files you can probably test this setup on a USB disk, just rename isolinux.cfg to syslinux.cfg, install syslinux to that disk, and boot from it. Once you have the directories right you can make a new bootable ISO out of the contents of the drive.

---

### Post by jabagawee on 2008-02-22
That was sooo vague, but I'll see what I can do. Anyone have comments for my setup? Or hints?

---

### Post by mrsteveman1 on 2008-02-22
Vague? What exactly do you need then?

---

### Post by Therion on 2008-02-22
> **jabagawee said:**
> That was sooo vague ... 

!!!

That word... "Vague"; I don't think it means what you think it means.

---

### Post by jabagawee on 2008-02-22
For example, anyone wanna tell me how isolinux works? If I learned just that, and I checked Google, I'd be most of the way there. Which files do I need from this syslinux archive? What's the syntax? Can I see some examples? etc.

---

### Post by mrsteveman1 on 2008-02-22
Isolinux is a bootloader for booting linux and other things such as freedos images, from an el-torito bootable cd-rom.

It's fairly simple to use, like i said the ubuntu cd has a perfect example of what a config looks like, so check the cd for isolinux.cfg. Basically there are menu entries for specific things, but all of them include a kernel and an append line, which sets various options.

There is some basic info [here]("http://syslinux.zytor.com/iso.php")

Heres an example of a simple entry for the ubuntu livecd (i cut it down a bit):

```
DEFAULT /casper/vmlinuz
LABEL live
  menu label ^Start or install Ubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel /install/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1

```

Basically for each disto you want on the cd you only need to keep the kernel, the initrd, and the filesystem image. Note that the kernel and initrd all have to be separate because the kernel for ubuntu will not work with another distro because once the system is running the kernel modules wont load right.

I would suggest you simply work around the ubuntu livecd and add the files from the others to the directory.

---

### Post by TravMan63 on 2008-02-22
That's a great list - I've tried quite a few of those distros...

You may want to look at SAM (PCLinux I believe)

I'd look really hard at elive - it's very high on my list of favorite distros (Debian)

I think Puppy and DSL are far enough apart to include both

good luck! keep us up to date!

---

### Post by jabagawee on 2008-02-22
Thanks for the input. If I make all the entries in isolinux, how will I be greeted as I boot the DVD? Will there be a menu waiting for me to choose an option?

---

### Post by mrsteveman1 on 2008-02-23
If you use some of the options isolinux supports, yea, it will look just like the ubuntu livecd when it boots.

There are a nuimber of support files, for instance these lines in the config:

```
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt
```

bootlogo is an image in the /isolinux directory on the cd (not sure of the format) that will be displayed on boot, the f1-f10 files are text files that will be displayed if the user presses those keys, and the background string is a color. There are also font files, an isolinux.txt file that displays a welcome message, etc.

---

### Post by jabagawee on 2008-02-24
What is ubuntu.seed?

---

### Post by jabagawee on 2008-02-24
Oh god I feel like such an idiot. My first attempt at combining Ubuntu with Ophcrack ended with Ophcrack unbootable.
```
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL ubuntulive
  menu label ^Start or install Ubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL ubuntuoem
  menu label ^OEM install of Ubuntu(for manufacturers)
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper oem-config/enable=true initrd=/casper/initrd.gz quiet splash --
LABEL ophcrack
  menu label Ophcrack LiveCD Graphics mode (auto mode)
  kernel /ophcrack/boot/vmlinux
  append vga=769 initrd=/cdrom/ophcrack/boot/initrd.gz ramdisk_size=6666 root=/dev/ram0 rw autoexec=xconf;startx
LABEL memtest
  menu label ^Memory test
  kernel /install/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
```

Do you see it? It's in the Ophcrack lines... -face palm- It's vmlinuz, not vmlinux, stupid.

EDIT: Also, it seems I don't need the "/cdrom/" on the append line of Ophcrack. Anyone care to subscribe to follow my process?

---

### Post by jabagawee on 2008-02-24
Update: I have Ubuntu, Ophcrack, and DSL working in VMWare.

---

### Post by jabagawee on 2008-02-24
Anyone have hints on how to get Linux Mint working? It's an Ubuntu derivative, and its isolinux config lines are confusing me.

---

### Post by mrsteveman1 on 2008-02-24
Ill grab an iso copy of mint and look it over.

What does the isolinux.cfg look like on it?

---

### Post by mrsteveman1 on 2008-02-24
This is where you may find problems, the filesystem is mounted by the initrd itself, and since it expects to find the filesystem in /casper just like ubuntu, they might not coexist easily.

---

### Post by jabagawee on 2008-02-24
Meh. I declare Linux Mint to similar to Ubuntu to be useful to my CD. I also don't need to be doing any security auditing too often, so Backtrack gets removed too. I'll edit the first post to show that.

---

### Post by jabagawee on 2008-02-24
Major updates. Check teh first post for details. bump~

---

### Post by jabagawee on 2008-02-24
Done With Everything!!! Zomg Im Screaming Like An Ubernoob. But Im So Excited That I Did This Entire Project In A Day And A Night. If A Mod Feels Like It, Please Edit This Post To Be More Pleasing To The Human Eye Then Warn Me!!

---

### Post by maybeway36 on 2008-02-24
If you want, you can even add DOS floppy images (using memdisk). Who knows, they may come in useful, and they're only about 1.5MB max.
Just curious, with the distros you have  working, how big is your DVD?

---

### Post by jabagawee on 2008-02-24
check the first post for the list of distros. THe total size's about 2GB

---

### Post by hippo31 on 2008-02-29
Hi,

I'm also trying to make a multiboot but on an usb stick and only with SysrescueCd and an Ubuntu (Xubuntu).
So im really interested in the details of your syslinux.cfg (or isolinux, which seems to be the same but for CDs/DVDs) and again in your folders and files organisation on your DVD.
Did you make a dir by bootable distro ? Or not ? Which files MUST be on the root of the medium, etc ...

Thanks in advance.

---

### Post by jabagawee on 2008-03-15
I've been asked in a PM for my menu.list. Lemme remind you guys: LiveCDs don't use GRUB! They use ISOLinux! Here's my isolinux.cfg:

```

GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL ubuntulive
  menu label Ubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL ubuntuoem
  menu label OEM Ubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper oem-config/enable=true initrd=/casper/initrd.gz quiet splash --
LABEL ophcrack
  menu label Ophcrack
  kernel /ophcrack/boot/vmlinuz
  append vga=769 initrd=/ophcrack/boot/initrd.gz ramdisk_size=6666 root=/dev/ram0 rw autoexec=xconf;startx
LABEL dsl
  kernel /isolinux/linux24
  menu label Damn Small Linux
  append ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791 initrd=/isolinux/minirt24.gz nomce noapic quiet BOOT_IMAGE=knoppix
LABEL pcloslive
  menu label PCLinuxOS  
  kernel /pclos/isolinux/vmlinuz
  append livecd=livecd initrd=/pclos/isolinux/initrd.gz root=/dev/rd/3 acpi=on vga=788 keyb=us splash=silent fstab=rw,noauto
LABEL SysResCD
  kernel /sysrescd/isolinux/rescuecd
  append initrd=/sysrescd/isolinux/rescuecd.igz video=ofonly vga=5 cdroot
LABEL memtest
  menu label ^Memory test
  kernel /install/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
```

As for where all the files go, I've lost track of them. I just threw them all around and referenced them in isolinux.cfg. If you want me to help with a SysResCD/Ubuntu combo, I'll be glad to help. Just PM me if you still need the help.

---

### Post by jabagawee on 2008-04-24
I never meant for this thread to be a HOWTO. I don't plan on releasing a guide on how to repeat my process. If you guys really want to see how I did it, you'll have to settle with the isolinux.cfg I posted. Draw conclusions based on the lines of that file. If you guys really want to, and I have the time, I'll post my ISO file somewhere for your viewing pleasure. I just really don't have the time to write a step-by-step guide on how to do this. Also, the disk is really personalized. Each distro you try to add will have its own nuances on how to integrate it onto a disc. So yeah.

---

### Post by slowpoke115 on 2008-05-01
Hi, i'm trying to make a multiboot disk with some Windows images on it, can anyone help me with this (I now its an ubuntu forum).

I have 4 images in .iso format (ophcrack, opensuse, hard heron, server 2003 and ERD commander) the last two are obviously Windows based, 2 of these are install CD's and the other 2 are live and I've tried using magiciso to make a multiboot disk but get a bunch of errors.

I'm confused because my suse disk has isolinux but my suse CD has something entirely different. I've read a bunch of forums but almost all of them just use DSL and Windows. A link or something will do, I've already wrote to 3 forums and just got answers such as use grub...

Thanks for the help :)

---

### Post by mishathegoat on 2008-05-24
I ran across a post while searching for info on the subject. I'm about to go ahead and read through it but this should help a good amount of people out: [http://www.msfn.org/board/Super-Disc-Multi-Boot-Project-CD-DVD-Us-t94398.html](http://www.msfn.org/board/Super-Disc-Multi-Boot-Project-CD-DVD-Us-t94398.html)

@Slowpoke15
Maybe this will help? [http://www.msfn.org/board/Super-Disc-Multi-Boot-Project-CD-DVD-Us-t94398.html&p=636838#entry636838](http://www.msfn.org/board/Super-Disc-Multi-Boot-Project-CD-DVD-Us-t94398.html&p=636838#entry636838)
It explains how to add Windows installs with your (iso)linux multiboot CD

---

### Post by Jotnar on 2008-06-12
To help everyone out, here's a text file I put together telling what files (usually in the initrd) need to be changed for varying Linux live cds to support a multiboot cd.  I've verfied the various *buntus boot to the live cd but I have no idea if you can install off of the disc.  Let me know if anyone tries it.

Cheers

```
Chris D'Hondt (cmdhondt @ hotmail.com)
Changes to Support Multibooting Linux Live CDs on the Same Disc (30,MAY 2008)

This assumes that your disc label is "AdminToolkit" and that your linux directory
on the root of your disc is called LINUX.  Change as needed.

Almost all of these changes deal with editing files inside the initrd.
This file is usually a gzipped cpio or a gzipped ext2 image.

Knoppix    - use the knoppix_name and knoppix_dir cheatcodes on ISOLinux initrd boot paramaters.

DSL        - See Knoppix

Zenwalk    - need to change name of livecd.sgn and edit liblinuxlive to change LIVECDSGN and LIVECDNAME variables
	     from=/LINUX needs to be added on isolinux append line.
	     root password is ZenLive.

Fedora	   - Username is root, no password. initrd0.img is gzipped cpio.
             To unpack: $> mkdir /home/user/tmp
			$> mv initrd0.img initrd0.gz
			$> gunzip initrd0.gz
			$> cd tmp
			$> cpio -id < ../initrd0
			$> mv ../initrd0 ../initrd0_old
          
	     needed to change the sections in 'init' where it referenced the LiveOS directory.
	     ie.. OSMINSQFS, EXT3FS, SQUASHED. You also need to change the lines right above so
             the files can be found

	     To pack:
			$> cd /home/user/tmp
			$> find . | cpio --create --format='newc' > ../initrd0.img
			$> cd ..
			$> mv initrd0.img initrd0
			$> gzip initrd0
			$> mv initrd0.gz initrd0.img

Ubuntu	   - need to change casper in initrd/scripts
	     change all $Path/casper to $Path/LINUX/UBUNTU/casper
	     change $mountpoint/.disk/casper-uuid to $mountpoint/LINUX/UBUNTU/.disk/casper-uuid
	     change all $Directory/casper to $Directory/LINUX/UBUNTU/casper
	     See above (Fedora) for cpio extraction and compilation.

Kubuntu    - See Ubuntu

Linux Mint - See Ubuntu

OpenSuSE   - need to change config.isoclient file to point new location for
             openSUSE-10.3.i386*. Also need to change init and linuxrc so 
	     that LIVECD_CONFIG points to config.isoclient in the right place.
	     See above (Fedora) for cpio extraction and compilation.

Mandriva   - needed to modify linuxrc and change LABEL to AdminToolkit
	     also change /live/media/distrib.sqfs to correct path.

Clonegenius- need to change copy path in init under "Mounting Squashfs filsystem"
             ISOLinux append line needs SUBDIR=LINUX/GENTOO added

CloneZilla - add /live_media/LINUX/CLONEZILLA to live_media_path_checklist in 
	     pkg\opt_drbl.tgz\opt\drbl\conf\drbl-ocs.conf
	     add /live_media/LINUX/CLONEZILLA to possible_path variable in ocs-live.d/s03prep-drbl-clonezilla
	     add /live_media/LINUX/CLONEZILLA to possible_path variable in S99start-ocs-live in /etc/rcS.d
             put changed S99start-ocs-live in the root of initrd 
             need to change casper in initrd/scripts
	     change all $Path/casper to $Path/LINUX/CLONEZILLA/casper
	     change all $Directory/casper to $Directory/LINUX/CLONEZILLA/casper
             at the bottom (line right before the brace) create a new line and add 
             cp S99start-ocs-live "${rootmnt}/etc/rcS.d/"
             See above (Fedora) for cpio extraction and compilation.
	     
PCLinuxOS  - need to change linuxrc in initrd (ext2 image).
             Change $MNTCDROM/$BASEIMG$LOOPSEXT to $MNTCDROM/LINUX/PCLINUXOS/$BASEIMG$LOOPSEXT
             Change losetup $DEVLOOP $MNTCDROM/$BASEIMG$LOOPTYPE to losetup $DEVLOOP $MNTCDROM/LINUX/PCLINUXOS/$BASEIMG$LOOPTYPE
             Change all $MNTCDROM/livecd.sqfs to $MNTCDROM/LINUX/PCLINUXOS/livecd.sqfs

Kaspersky  - In init change ${cdrom_mount_point}${SUBDIR}/kavresc to ${cdrom_mount_point}${SUBDIR}/LINUX/KASPERSKY/kavresc
             Gentoo based.

Virtualbox is a good way to test your changes
To get eth0 interface working in VirtualBox, you need the Bridge_Utils package:

$> brctl addbr br0
$> ifconfig eth0 0.0.0.0
$> brctl addif br0 eth0
$> ifconfig br0 192.168.1.2 netmask 255.255.255.0


```

---

