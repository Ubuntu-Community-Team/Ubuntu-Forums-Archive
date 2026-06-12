---
title: "Boot ISO files from USB using Grub2 (simple point and click options) Fixed: 5th Oct"
date: 2016-08-03
forum: General Help
---

### Post by T2uiYKb7 on 2016-08-03
[B][COLOR=#ff0000]Update: 5th October 2016.

[/COLOR][COLOR=#008000]Darn it. One of the terminal commands was wrong. Maybe right from when I first posted this thread.[/COLOR]

[COLOR=#008000]If someone did this and couldn't mount the USB the word *"mount"* was missing from that terminal command, that's why it didn't work. Should work now from start to finish. [/COLOR][/B][B][COLOR=#ff0000]

[/COLOR][/B][B][COLOR=#ff0000]Update: 24th August 2016.

[/COLOR][COLOR=#006400]boot.cfg entries (in addition to the current Buntu (Ubuntu, Kubuntu etc.) ones entered in the tutorial.)[/COLOR]

[URL="https://github.com/thias/glim/tree/master/grub2"]https://github.com/thias/glim/tree/master/grub2

[/URL][B][URL="https://wiki.archlinux.org/index.php/Multiboot_USB_drive"]https://wiki.archlinux.org/index.php/Multiboot_USB_drive

[/URL][/B][COLOR=#006400][B]I haven't tested most of these, read the ArchLinux.org entries carefully as they sometimes ask to make slight changes to new Distro versions.

[/B][/COLOR]
**-------------------[B]-------------------[B]-------------------[B]-------------------[B]-----**[/B][/B][/B][/B][URL="https://github.com/thias/glim/tree/master/grub2"]
[/URL]
[/B]
There are a few Grub2 to ISO tutorials out there but they are pretty intimidating so I made my own as simply as I could.

[B]It's handy as there's no limit to how many ISOs you can add to your drive as long as you add a correct grub.cfg entry. You can use the rest of your drive for whatever you want (documents, movies, music etc.) as it doesn't need to be formatted for new ISOs.
[/B][SIZE=4]
[/SIZE][COLOR=#800080][SIZE=3]**Create bootable USB drive:**[/SIZE]
[/COLOR]
**[COLOR=#800080][SIZE=4][SIZE=3]1.[/SIZE])[/SIZE][/COLOR] [COLOR=#0000ff]Install Gparted via Software Center[/COLOR] **or Synaptic

or open terminal and type [COLOR=#009933]***sudo apt install gparted***[/COLOR] *(enter)*

[COLOR=#800080][SIZE=3]**2.) **[/SIZE][/COLOR]Create a FAT32 partition on your desired USB drive using Gparted and change it's flag to boot . **(Right click partition to view options)**

**To clarify, you want you want your USB drive to have a single FAT32 partition with no files on it and a boot flag.**[COLOR=#ff0000][SIZE=2] (Note: Removed line saying other file systems can be used, this is not always true and better safe than sorry.)[/SIZE][/COLOR][B][COLOR=#800080]

**[COLOR=#800080]Take note of it's name " [/COLOR][SIZE=3][COLOR=#006400]sd[/COLOR][COLOR=#0000cd]x[/COLOR][COLOR=#006400]1[/COLOR][/SIZE][COLOR=#800080] "[/COLOR]**

[SIZE=3]3.) [/SIZE][/COLOR][/B]Create a folder called [COLOR=#0000ff]**isoboot**[/COLOR] in the [COLOR=#0000ff]**/mnt/** [/COLOR]directory either by giving your file manager sudo privileges then immediately closing it when done ***( eg. *[COLOR=#0000ff]*sudo nautilus*[/COLOR]* from terminal or*[COLOR=#0000ff]* gksu *[/COLOR]*from terminal, then entering*[COLOR=#0000ff]* nautilus *[/COLOR]*)***

or open terminal and type [COLOR=#339933]***sudo mkdir /mnt/isoboot***[/COLOR] *(enter)*

**[COLOR=#800080][SIZE=3]4.) [/SIZE][/COLOR]**Open terminal and type* **[COLOR=#008000]sudo [/COLOR][COLOR=#008000]mount[/COLOR]**[COLOR=#009933]** /dev/sd**[/COLOR][COLOR=#0000ff]**x**[/COLOR][COLOR=#009933]**1 /mnt/isoboot**[/COLOR] (enter)*

**(replace the *[COLOR=#0000ff]x[/COLOR]* with the letter of your [COLOR=#0000ff]desired drive[/COLOR] as listed in Gparted)**

[COLOR=#800080][SIZE=3]**5.) **[/SIZE][/COLOR]Open terminal and type:

[COLOR=#009933]***grub-install --force --no-floppy --boot-directory=/mnt/isoboot/boot /dev/sd***[/COLOR][COLOR=#0000ff]***x ***[/COLOR]*(enter)*[COLOR=#009933]
[/COLOR]
[B](replace the *[COLOR=#0000ff]x [/COLOR]*with the letter of your [COLOR=#0000ff]desired drive [/COLOR]as listed in Gparted, be very careful to use the correct letter, you do not need to type the "1" after it)
[/B]
Your done as far as making it boot to a Grub menu.


[SIZE=3][COLOR=#800080]**Add ISO files:**[/COLOR][/SIZE]

[COLOR=#800080][SIZE=3]**1.) **[/SIZE][/COLOR]Download an Ubuntu (or Xubuntu, Kubuntu, Mythbuntu, Lubuntu etc.) .iso file as you normally would.

[SIZE=3][COLOR=#800080]**2.) **[/COLOR][/SIZE]Open your file manager and create a "***iso***" folder on your newly made USB.

[COLOR=#800080]**[SIZE=3]3.)[/SIZE] **[/COLOR]Copy and paste the .iso you downloaded into that "***iso***" folder using your file manager.
[COLOR=#800080]
[SIZE=3]**4.) **[/SIZE][/COLOR]Open the [COLOR=#0000ff]***/boot/grub/grub.cfg***[/COLOR] file on your USB drive (browse to it with you file manager and double click on it)

[COLOR=#800080][SIZE=3]**5.) **[/SIZE][/COLOR][SIZE=3][SIZE=2]Add the text below, depending if the the ISO is for a 64 bit or 32 bit version of Ubuntu.
[/SIZE][/SIZE][COLOR=#d3d3d3].[/COLOR]
For a **32bit ISO** copy and paste the following exchanging the words [COLOR=#0000ff]**ubuntu_32bit_file.iso**[/COLOR] for the [COLOR=#0000ff]**actual filename**[/COLOR] of the .iso you have copied into the iso folder of your USB drive. Change the words [COLOR=#0000ff]***32bit ISO Description ***[/COLOR]to whatever you want to describe your ISO.

Text:

[I][B][COLOR=#006400]menuentry '[/COLOR][COLOR=#0000ff]ubuntu_32bit_file.iso[/COLOR][COLOR=#006400]' {


set isofile="/iso/[/COLOR][COLOR=#0000ff]ubuntu_32bit_file.iso[/COLOR][COLOR=#006400]"


loopback loop (hd0,5)$isofile


linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject


initrd (loop)/casper/initrd.lz


}[/COLOR][/B][/I]

For a** 64bit ISO** copy and paste the following exchanging the words [COLOR=#0000ff]***ubuntu_64bit_file.iso***[/COLOR] for the **[COLOR=#0000ff]actual filename[/COLOR] **of the .iso file you have copied into the "iso" folder of your drive. Change the words [COLOR=#0000ff]***64bit ISO Description ***[/COLOR]to whatever you want to describe your ISO.
[B][COLOR=#336666]
[/COLOR][/B]Text:[B]
[COLOR=#006400][I]
menuentry "[/I][/COLOR][COLOR=#0000ff]*64bit ISO Description*[/COLOR][COLOR=#006400][I]' {


set isofile="/iso/[/I][/COLOR][COLOR=#0000ff]*ubuntu_64bit_file.iso*[/COLOR][COLOR=#006400][I]"


loopback loop (hd0,5)$isofile


linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject


initrd (loop)/casper/initrd.lz


}
[/I][/COLOR][/B]


[B]Your finished. Reboot your computer and configure BIOS to boot your USB (pressing F12, F2, esc or del generally opens your BIOS menu or a BIOS boot menu but [COLOR=#800080]Google your PC model before you reboot to save the hassle.)[/COLOR]
[/B]
[I]Any Linux ISO that supports booting from Grub2 can be booted this way but the Grub2 entry will differ more than simply changing the file name.
[/I]
Any recommendations as to how to make this even more simple are much appreciated.
[SIZE=2][B][COLOR=#d3d3d3].
[/COLOR]
PenDriveLinux.com is where I originally read about the Grub2 ISO method so credit goes to them although this is not a copy and paste.

If your totally comfortable with command line (or don't mind copying and pasting everything and anything) you can get that method [here]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/"). Although there *grub.cfg* entries and *wget *(download) commands are for an older version of Ubuntu.[/B][/SIZE]

---

### Post by him610 on 2016-08-03
Welcome to Ubuntu Forums. First post is a tutorial - that's great. 

You might consider moving, or posting tutorials down in the Tutorial Forum.

---

### Post by T2uiYKb7 on 2016-08-03
Cheers. Will do.

---

### Post by yancek on 2016-08-03
FAT32 is the standard on flash drives but booting an iso file can be done regardless of the filesystem type.
I use a separate partition for iso files and just put entries to boot them in the grub.cfg file on the hard drive to test them.
I've never found it necessary to mark a partition "boot" in GParted unless I am using some type on windows installer.  Linux systems generally don't need the boot/active as windows does but of course using won't be any problem.

As far as making it simpler, you don't need a separate iso directory on the flash drive, just copy to the root of the partition.  Obviously though, either will work as long as the path is correct.
Set your web browser to download the file directly to that partition, save the trouble of copying.

Good job, a simple and straight forward tutorial.

---

### Post by T2uiYKb7 on 2016-08-04
> **yancek said:**
> FAT32 is the standard on flash drives but booting an iso file can be done regardless of the filesystem type.
I use a separate partition for iso files and just put entries to boot them in the grub.cfg file on the hard drive to test them.
I've never found it necessary to mark a partition "boot" in GParted unless I am using some type on windows installer.  Linux systems generally don't need the boot/active as windows does but of course using won't be any problem.

As far as making it simpler, you don't need a separate iso directory on the flash drive, just copy to the root of the partition.  Obviously though, either will work as long as the path is correct.
Set your web browser to download the file directly to that partition, save the trouble of copying.

Good job, a simple and straight forward tutorial.

Heya, yeah I've used EXT4 in the past I was just hesitant use EXT4 or NTFS in the tutorial as Mac's, Android and TVs may not be able to read/write to it and it's handy to have an all purpose USB.

I've only come across two PCs  that needed the boot flag in my time with Linux one being the one I'm using at the moment (Samsung laptop from in 2012) your right in saying it's very uncommon I just thought better safe than sorry.

Thanks for the compliment.

I used the ISO folder folder to keep things tidy, it's also on the Ubuntu Grub2Iso man page which is what first used for boot.cfg entries.

**Edit: To be honest although I haven't had any issues with using an EXT4 partition for this I felt some pressure to specifically state FAT32 as every other tutorial on the internet does. I thought maybe there may be an issue with old hardware and EXT4 (or some issue somehow with EXT4 and NTFS in some cases) but I guess everyone just copied each other. **:)

---

### Post by yancek on 2016-08-04
FAT32 is better because it can be used with Linux, windows and mac so if a person wants a bootable flash compatible with all, FAT32.

I understand that the BIOS on some computers does require the active/boot be set although it apparently is pretty limited.  Lucky you to have found one.

Having a separate 'iso' directory is a good idea, particularly if you were to have some Linux systems that were not directly bootable from an iso and needed to be extracted to boot.  That could get pretty messy.  Most of the tutorials I've seen also do the same, a separate 'iso' partition.  My point was simply that it wasn't necessary which I'm sure you know.

---

### Post by T2uiYKb7 on 2016-08-07
I found a Sourceforge project that made a GUI program using Grub2 to boot ISOs, I think that's unnecessary but it had a great list of boot.cfg entries, 20 plus.

I can't find it now, it was a little made up word like Glimph or something (probably not helpful.)

---

### Post by yancek on 2016-08-07
Have you used YUMI which is at the pendrive (UUI) site?  Sound similar.  I have a list of grub.cfg entries for about 30 Linux utilities and Live CD iso files which I have tested.  Generally I use the booting of an iso to install systems to test when new distributions come out.

---

### Post by oldfred on 2016-08-07
I started booting ISO before most of the scripts.
I followed what became this, I use same type of entry for flash drive as another partition on hard drive:

 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive) 

Arch link above has link to this:

        GRUB2 Live ISO Multiboot
[https://github.com/thias/glim](https://github.com/thias/glim)

---

### Post by T2uiYKb7 on 2016-08-23
> **yancek said:**
> Have you used YUMI which is at the pendrive (UUI)  site?  Sound similar.  I have a list of grub.cfg entries for about 30  Linux utilities and Live CD iso files which I have tested.  Generally I  use the booting of an iso to install systems to test when new  distributions come out.

Cool. Would you mind posting that boot.cfg list you've tested?

> **oldfred said:**
> I started booting ISO before most of the scripts.
I followed what became this, I use same type of entry for flash drive as another partition on hard drive:

 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive) 

Arch link above has link to this:

        GRUB2 Live ISO Multiboot
[https://github.com/thias/glim](https://github.com/thias/glim)

Yeah I understand there is already  tutorials but I found them unnecessarily  complicated (using wget, echo, and mkdir and cd when someone with no Linux (or Windows CMD) knowledge can easily do the same with GUI.)[B]

Awesome! Glim is the one I was thinking of (Glimph isn't too far off but I  was searching Sourceforge not GitHub) thanks for that oldfred. The most reliable boot.cfg entires I've found.
[/B]

---

### Post by yancek on 2016-08-24
The grub.cfg entries I've tested successfully are in the attached file.  As you can see, most of the Ubuntu derivatives are almost identical changing only the iso name and path as well as the drive/partition entry.  There are other entries which work, these are just the ones I have tested.  There are some Linux distributions which will not boot directly from an iso but can be extracted and copied to a partition and booted.  Some of the entries are just installers, others are Live CD and installer.  Comments are in the file.

[ATTACH]270846[/ATTACH]

---

### Post by sudodus on 2016-08-24
Nice start at our Ubuntu Forums with a tutorial :-)

> **andrew.nz said:**
> I've only come across two PCs  that needed the boot flag in my time with Linux one being the one I'm using at the moment (Samsung laptop from in 2012) your right in saying it's very uncommon I just thought better safe than sorry.

I have found that several middle-aged HP computers want a boot flag to boot from USB via grub at least from linux (ext{2,3,4}) partitions. It *should not* be like that, but it *is*, so I agree, that it is good to set the boot flag. Those HP computers are also unwilling to boot from USB via grub from drives with a GUID partition table, at least there are problems in BIOS mode.

Only once I had problems with a pendrive with an MSDOS partition table and a FAT32 partition because of the boot flag. It was a brand new installed Windows 7 system, that did not mount the pendrive. But when I had made it up to date with security updates and bugfixes, Windows 7 was happy to mount it.

---

### Post by T2uiYKb7 on 2016-08-25
> **I have found that several middle-aged HP computers want a boot flag to boot from USB via grub at least from linux (ext{2,3,4}) partitions. It *should not* be like that, but it *is*, so I agree, that it is good to set the boot flag. Those HP computers are also unwilling to boot from USB via grub from drives with a GUID partition table, at least there are problems in BIOS mode.

Only once I had problems with a pendrive with an MSDOS partition table and a FAT32 partition because of the boot flag. It was a brand new installed Windows 7 system, that did not mount the pendrive. But when I had made it up to date with security updates and bugfixes, Windows 7 was happy to mount it.[/QUOTE]

True. So Windows 7 didn't like mounting a USB as a normal drive **with** the boot flag?

I just noticed today that Window 10 will mount **multiple **partitions on a removable drive. It seems like a given being on Linux but it hasn't been the case until very recently, Microsoft has it documented even that only the first FAT/NTFS partition will be mounted in the past. It's great they finally did it, it was obviously an artificial limit they imposed for god knows why.

[QUOTE=yancek said:**
> The grub.cfg entries I've tested successfully are  in the attached file.  As you can see, most of the Ubuntu derivatives  are almost identical changing only the iso name and path as well as the  drive/partition entry.  There are other entries which work, these are  just the ones I have tested.  There are some Linux distributions which  will not boot directly from an iso but can be extracted and copied to a  partition and booted.  Some of the entries are just installers, others  are Live CD and installer.  Comments are in the file.

[ATTACH]270846[/ATTACH]


Cheers. If the vmlinuz and intrid.lz are the root of a directory of the ISO (not /casper or /live) what do I put as the boot=? (Can't be boot=casper or boot=live.)  Ubuntu compatible Puppy has them in the root, is it boot=/ ?

---

### Post by yancek on 2016-08-25
I haven't used Puppy for years.  In the past I would extract the iso and copy it to a partition and boot it that way.   If you look at the entries  I posted, a number of them do not have any "boot" section and I don't know that you would need it with Puppy.  What you need to be pointing to is the kernel, vmlinuz ususally.  I haven't tried booting a Puppy iso directly.   The entry below boots but requires the Puppy iso to be loop mounted then copied to a puppy directory in the root of the partition, in this case sdb3.

menuentry "puppy tahr" {
insmod part_msdos
set root='(hd1,msdos3)'
linux /puppy/vmlinuz pfix=ram
initrd /puppy/initrd.gz 
}

---

