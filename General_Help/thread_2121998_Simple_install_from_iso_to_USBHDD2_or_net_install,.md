---
title: "Simple install from iso to USB/HDD2 or net install, missing steps?"
date: 2013-03-03
forum: General Help
---

### Post by Luxx on 2013-03-03
I'm trying to install a new distro on my first HDD. This computer has 2 HDDs currently. None of the methods I can find online actually work. Please help. It has taken over a week to download an iso, create a live USB that doesn't work, and find out I couldn't expect the USB to boot anyway because there is nothing to boot it with anywhere in the USB that the computer can recognize. That seems like a HUMONGOUS glaring oversight in the USB programs and tutorials.

I downloaded isos for several distros and can't get any of them to work, although I finally did manage to get a USB to LOOK like it should work.
Ultimate Edition 3.5
Linux Mint Nadia
Bhodi Linux
Fuduntu

After trying several USB creator programs Unetbootin actually resulted in a USB boot that tried to do something. I got some SYSLINUX  message mentioning H. Peter Anvin, blah blah. After googling for hours I discovered the USB needs syslinux and found advice to change isolinux to syslinux, but intructions were vague or missing a step or two. I tried using dd, which got the USB stick labelled correctly and got me to the devices list, but not quite to boot either. 

After learning the USB needed syslinux or some kind of boot loader, I decided to try to find out 3 things:
1)	Could the iso be copied directly to the other HDD using dd and then install, skipping a CD or USB? Theoretically, yes, but I still need a MBR and I'm not quite sure how to set up the partition for the boot loader and get it installed prior to first boot.

2)	How to get the correct bootloader installed on the USB to make it truly bootable (syslinux vs. isolinux), and

3)	How to do a net install. I thought I remembered years ago that the standard method for installing Linux was to pull it directly from repositories or servers and install directly to the computer. I know some distros can do this now, but haven't been able to find instructions that seem complete. 

I just want to note that the dd method is MUCH SIMPLER than downloading Unetbootin and figuring out how to make it find and recognize your iso files and devices. Type a few simple words of code and it's done. Forget about the programs that "automate" everything. Terminal already automates things if you just use it. I would really prefer to know how to do it the right way than have a script or program do it all for me and leave me completely in the dark when something is incomplete and it doesn't work. So if you know some code or tutorials I haven't found I would be very grateful.

---

### Post by oldfred on 2013-03-04
Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Some old versions of Ubuntu had installers with issues.

 Bugs in usb-creator unetbootin is an alternative if usb-create does not work
[https://bugs.launchpad.net/ubuntu/+source/usb-creator](https://bugs.launchpad.net/ubuntu/+source/usb-creator)


Are you using a new version of unetbootin? Some older versions did have issues. 
Also it just seems some flash drives, some BIOS in combination do not work.
      
 [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Some of the possible fixes:

 syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
in the directory from "isolinux.cfg" to "syslinux.cfg"
[http://ubuntuforums.org/showthread.php?t=2078599](http://ubuntuforums.org/showthread.php?t=2078599)
Try replacing the file vesamenu.c32 on the USB disk drive with that one "/usr/lib/syslinux/vesamenu.c32" of Ubuntu Maverick system or use UNetbootin than works fine.
[http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/)

Are you using USB3 port? Some have issues with those.

Not all distributions are hybrid:
      
 The daily ISOs for the Ubuntu Oneiric 11.10 development cycle (and all official Ubuntu CD releases going forward)
for i386 and x86_64 platforms will be now spun as hybrid ISOs. or you can use dd
[http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid](http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid)

---

### Post by Luxx on 2013-03-05
Thank you for the links. I had come across some of these, but there are a few I had missed. I'm reviewing info concerning syslinux and grub. It seems dd should work to put any distro iso on a USB stick, but there may be some things I have to do manually to get it to boot. I am finding no syslinux on USB or in the isos. Once I wrap my head around this to the point I can implement the instructions I will get back. Again, thanks. I have a few things to try out.


Wonderful. I can no longer rename or edit anything. Nautilus won't run as root (pretends to but won't do anything). It worked yesterday, but Synaptic was acting funny. I lost most of my GUI and had to reinstall ubuntu-desktop.

---

### Post by Luxx on 2013-03-09
Here's where I'm at:

Several of the above links offer suggestions that seem feasible, but  I can't get any of them to work. I made a serious mistake when I upgraded my system. Priviledges in Nautilus (gksudo nautilus) no longer work and I cannot change file names, make changes in files, or add or replace them, so even though some of these syslinux or vesamenu.c32 options seem like they might be along the right path, I can no longer try them. I could have done this before I upgraded my system. 

Trying the updated version of Unetbootin did not make any difference. I was trying to use dd to do this anyway, because when a pre-made program doesn't work it just doesn't work. When you do something in terminal with some knowledge and intent, you can usually figure out what you missed, what went wrong, and why it didn't work. That was why I said I wanted to know how to "do it right" from terminal. I don't really find pre-made solutions simpler than using the terminal. They just leave me in the dark.

At this point I am leaning towards: 

1) a net install (I have found instructions for a net install, but there seems to be a very important piece or pieces missing)

or

2) installing grub on the second hard drive with the iso and installing it directly to HDD2. I have not found enough info to put together how to do this, although I have found that it is theoretically possible and it doesn't seem like it should be that hard.

I found a friend with a Windows computer and tried to use the Windows version of Unetbootin, but then discovered the USB port didn't work on that computer. I am running out of options.

---

### Post by oldfred on 2013-03-09
I now only use hard drive install or from one drive to another using grub2's loopmount.

 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

I now only have one entry in grub's 40_custom so I can more easily edit the file I am changing ISOs in. It is on my 2nd drive in 4th partition in a /iso folder, so that is why it refers ot (hd2,4). Text file I edit is livecdimage.cfg.

```
 # livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd2,4)/iso/livecdimage.cfg
#} 
# Add iso names to livecdimage.cfg
#for i in `ls *.iso`;do echo "# "$i>>livecdimage.cfg; done;

    menuentry "Ubuntu 12.04.2 Precise Desktop ISO 64bit" {
    set isofile="/boot/ISO/ubuntu-12.04.2-desktop-amd64.iso"
    loopback loop (hd0,5)$isofile 
    linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile 
    initrd (loop)/casper/initrd.lz
}

    menuentry "Uubuntu 12.10 Quantal ISO 64bit" {
    set isofile="/iso/quantal-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

     menuentry "Parted Magic (Boot ISO Image via Grub2) " {

 insmod part_gpt
set isofile="/iso/pmagic_2012_05_30.iso"
loopback loop (hd2,4)$isofile
linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off load_ramdisk=1 prompt_ramdisk=0 rw vga=normal loglevel=9 max_loop=256 vmalloc=256MiB
initrd (loop)/pmagic/initrd.img

 }
   menuentry "gparted (Boot ISO Image via Grub2) " {

 insmod part_gpt
set isofile="/iso/gparted-live-0.12.1-5.iso"
loopback loop (hd2,4)$isofile

 #	linux (loop)/live/vmlinuz live-media=iso=$isofile keyb=us gl_kbd=us gl_lang=en_US gl_numlk=off gl_batch boot=live union=aufs  #toram=filesystem.squashfs noswap noprompt vga=791
#        linux (loop)/live/vmlinuz fromiso=$isofile boot=live noswap
        linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs
 initrd (loop)/live/initrd.img

 }
# linux /workdir/vmlinuz fromiso=/dev/sda11/debian-live-6.0.3-i386-lxde-desktop.iso boot=live config BOOT_IMAGE=/live/vmlinuz
   menuentry "Boot-Repair ISO 64bit " {

 insmod part_gpt
set isofile="/iso/boot-repair-disk.iso"
loopback loop (hd2,4)$isofile

     linux (loop)/live/vmlinuz2 boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs
#    linux (loop)/live/vmlinuz2 boot=live config
 initrd (loop)/live/initrd2.img

 }
    menuentry "SystemRescue CD on hard drive" {
              set root=(hd2,4)
              linux   /sysrcd/rescuecd subdir=sysrcd setkmap=us
              initrd  /sysrcd/initram.igz
} 

    menuentry "Reboot" {

 reboot

 }
   menuentry "Halt" {

 halt

 }
```

---

### Post by Luxx on 2013-03-10
This looks like exactly what I was looking for. Thanks for the links. After some reading homework and trial-and-error, I'm sure I'll have some questions. I'll give this a try and get back.

---

### Post by Luxx on 2013-03-15
Ummm... curious. I put in a 3rd HDD and it wants to mount it at /usb/floppy. It's SATA. I don't even know what to think of that.

---

### Post by oldfred on 2013-03-16
I have seen users have issues with Asmedia SATA ports. Not sure why a hard drive plugged into a SATA port would be seen as USB?

---

### Post by gordintoronto on 2013-03-16
I've used Unetbootin many times, and it has always produced a USB flash drive which booted into a Live session -- including Mint Nadia and Fuduntu. Have you checked the checksum of the ISOs you downloaded?

There is a lot of nonsense on the Internet, and it sounds you are paying too much attention to it.

---

### Post by Luxx on 2013-03-30
Sums checked, Unetbootin and the USB creator did not work. There was a syslinux error; USB would not boot. I don't see anything wrong in trying to understand why they didn't work or how to use a different method. I would prefer a different method and to know how and why it works.

---

### Post by oldfred on 2013-03-30
Are you using old versions? Or USB3 ports?

There were bugs with the installer a couple of years ago (or if you have files from 10.04).

Some also just have issues with certain flash drives.
       Post #14 some flash drives that did not work

Really old bugs.
      
 syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
in the directory from "isolinux.cfg" to "syslinux.cfg"
[http://ubuntuforums.org/showthread.php?t=2078599](http://ubuntuforums.org/showthread.php?t=2078599)
Try replacing the file vesamenu.c32 on the USB disk drive with that one "/usr/lib/syslinux/vesamenu.c32" of Ubuntu Maverick system or use UNetbootin than works fine.

    
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)

---

### Post by Luxx on 2013-03-30
I'm thinking I need to put an extra partition on the drive I want to install the ISO on, and install grub in that partition? 

But the instructions seem to be telling me to modify my existing grub file on THIS drive so I can install the ISO to the drive I am currently on? I don't want to install on this drive (sda) I want to install on a different drive (sdc).

This is what I meant by missing steps. The instructions all seem to be there, just the connection from one thing to the next are assumed instead of explained. 

So I'm assuming I really want to install grub somewhere on sdc and not just modify the grub file on sda. 

So I'm playing with it, but afraid of accidently installing on the drive I'm using.

---

### Post by oldfred on 2013-03-30
I have grub on every drive. But I modify the grub I normally boot from to include the grub entry to loopmount an ISO. You do not install grub to partitions. Its boot loader goes into the MBR.
Only if installing just grub without a system, then you install grub to that device. But you have to manually create a grub.cfg as the extra grub folders with scripts and parameter settings are not installed (they are part of Ubuntu).

You just do not want the ISO in the partition you want to install into. And best not on same drive. But if not in an extended partition so you are not mounted the extended, it should even work on same drive. 

So where are you installing it?
To simplify my changes to grub I now use this in my grub. But I boot from sdc. From grub the boot drive is hd0. So my sdb drive becomes hd2 and I have my /iso/ folder in my 4th partition. The I create a text file in my iso folder so I can edit it with changes and never have to edit 40_custom again.


       gksudo gedit /etc/grub.d/40_custom
    
menuentry 'Live ISOs' {
configfile (hd2,4)/iso/livecdimage.cfg
} 

Then livecdimage.cfg is this:

```
# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd2,4)/iso/livecdimage.cfg
#} 
# Add iso names to livecdimage.cfg
#for i in `ls *.iso`;do echo "# "$i>>livecdimage.cfg; done;

menuentry "Ubuntu 13.04 Raring ISO 64bit" {
    set isofile="/iso/raring-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```

---

### Post by Luxx on 2013-03-30
The ISO is on the drive I'm using now, sda1, and I want to install the new OS to empty hdd sdc.

Adding the menuentry to 40_custom doesn't seem to do anything. I can't mount the specified ISO from the specified location.
What is the user supposed to do in order to get the ISO to mount after adding the menuentry? Is it different from just booting the computer?

---

### Post by oldfred on 2013-03-31
You should just be able to boot the ISO.

But you have to have drive numbering and path correct in grub when you reboot. Sometimes that takes a bit of experimenting depending on errors you get. If you have /iso folder in same drive and first partition then the drive in grub will be hd0,1. Where did you create the iso folder? And it cannot be the path as you see it in Ubuntu because that is after Ubuntu has mounted it.

And did you create the liveimage.cfg file in the /iso folder?

Use e on grub menu to see the boot stanza you have created and edit if need be.

---

### Post by Luxx on 2013-03-31
Oh, my... I can't believe how simple it really was.

When it didn't seem to be working at first I was about to go through all kinds of trouble-shooting and re-reading, etc. when I ran across a little tip I hadn't noticed before. It appears all I had to do was **_hold down the shift key_** so the grub menu would come up, and there it was. I installed Ultimate Edition to sdc and it worked beautifully, until I tried to get back into my hard drive, sda. 

Now Ultimate Edition has taken over my computer completely. I can't get back into the hdd I was in before. It doesn't boot. I can only boot into the 3rd drive now.

...and I can't even see my other drives from this one except in the partition manager. Maybe this was a really bad idea. I hope I can get back into my Ubuntu.

---

### Post by oldfred on 2013-03-31
When you have multiple drives, you have to always use Something else or manual install just to get the combo box that gives the option on which drive's MBR to install grub2's boot loader into.Then you have to change BIOS to boot from that drive.

From new install you can reinstall grub to sdc.
sudo grub-install /dev/sda


But grub also remembers where to reinstall on major updates. This will reset that: #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions


New version's grub should show your old install. Boot into old install and from it reinstall grub to sda.

 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by Luxx on 2013-03-31
Absolutely lovely! And with that, I am convinced that this really was an easier way to install a new OS to an additional hard drive.

The first time through may present a bit of a learning curve to someone who has never done it, but it's worth doing it this way if it's something you would use frequently.

Thank you so much for your expert guidance.

---

### Post by oldfred on 2013-03-31
Glad you got it working. 

It more is that you have to be already booting with grub, and have another drive. And be willing to edit grub's 40_custom and some understanding of paths, partitions and mounts. A lot of users find all that way too complicated. Some distributions do not loopmount, but many do, but it can be a bit of a search to find the correct boot options.

But if installing often like with raring or just testing a new install it can be a lot quicker way to install.

I used flash drive before I converted to my other hard drive. But also find it a lot easier to just copy a new ISO to my /iso folder and edit my file to have the new name. I also easily add other ISOs and with my flash drive have many ISO as a full repair flash drive.

---

