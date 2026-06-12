---
title: "installing wubi to a USB hard drive"
date: 2007-11-13
forum: General Help
---

### Post by gubemton on 2007-11-13
Hello, my internal drive only has 19GB free at the moment, and i was wondering if i could install WUBI to my external USB hard drive, or if i had to install it on my main hard drive. thanks in advance

---

### Post by ago on 2007-11-13
should be ok, try 7.10 first

---

### Post by Rajan Varadarajan on 2008-04-15
I have a Toshiba Satellite M45-S331 laptop. The BIOS doesn't allow USB booting (wish it did!). Recently I bought a Western Digital 250GB Passport drive and would like to install ubuntu on it. This way, I can keep my Windows XP Pro on the main drive of the laptop.

I downloaded Wubi beta and ubuntu 8.04 beta and started wubi. It did provide me with the option of ubuntu or WinXP at startup but ran into all kinds of errors. Wubi could not install ubuntu on the passport drive; kept getting grub4Dos error and other errors.

Question:
1. The passport drive is FAT32 and I am willing to dedicate at least half of it for ubuntu.
2. How can I set up partition the USB drive and install ubuntu on it?
3. Since I don't have USB boot option in the BIOS, I would like to use Wubi to start ubuntu but would like a full install including grub on the passport drive.
4. I tried to install 7.10 version but it failed; went into an endless loop of install screens (from partitioning to grub install) and then I simply quit.

Thanks much in advance.

Rajan Varadarajan

+++++++++++++++++++++
Ago (I suppose that is Agostino - the creator of Wubi??) - thanks much.
Question: I am going to wait for the full release of 8.04. But, in view of your comment, I am envisioning a scenario like this -
1. Install Wubi in one of the folders.
2. Running Wubi establishes the option in the boot menu to go between XP and ubuntu.
3. Do a full install of ubuntu on the external passport hard drive; grub is going to be installed on the main hard drive so if I select ubuntu in the boot menu, grub can be run from the hard drive and the full ubuntu can be loaded from the passport drive.
<the major question is: will installing grub wreck my XP? even if there is a remote possibility, I don't want to risk it:-)>
4. Install other ubuntu apps as needed on the passport drive.

Will this scenario work? Thanks again.

---

### Post by ago on 2008-04-16
If the bios cannot boot off the USB disk, then even installing full Ubuntu you will not be able to boot. If you want to boot you need to have a small boot partition on your fixed disk,  grub will also sit on the fixed disk.

---

### Post by iamclueless on 2008-04-17
does anyone have instructions on how to do this?

boot a USB device when the board does not support a USB boot

my limited understanding of grub and linux leads me to believe it is possible.  I imagine it involves a sepate boot partition... with grub directing the boot to the usb device.

i know it can be done with Puppy Linux.... but thats a bit different.

how would it be done if say you wanted to run 2 OSs in your internal drive and one or a few more from an external drive.

thanks in advance

---

### Post by Rajan Varadarajan on 2008-04-18
> **iamclueless said:**
> does anyone have instructions on how to do this?

boot a USB device when the board does not support a USB boot

my limited understanding of grub and linux leads me to believe it is possible.  I imagine it involves a sepate boot partition... with grub directing the boot to the usb device.

i know it can be done with Puppy Linux.... but thats a bit different.

how would it be done if say you wanted to run 2 OSs in your internal drive and one or a few more from an external drive.

thanks in advance

Exactly. This is the problem with pre-2006 laptops; I was told that most laptops manufactured after 2006 have motherboards with USB boot capability in BIOS.

For other laptops, I have scoured the message boards widely. The short answer is - it is technically possible but you have to make a boot CD, have grub installed in the fixed hard drive (this is my major question/worrry - would grub wreck the operation of XP installed in the MBR?). But the number of hoops one has to jump in making boot from an external hard disk is very large and is more prone to errors. This is where I thought wubi hit the bull's eye. I have explained in my earlier post exactly what I want to accomplish. Can wubi do it? I don't know. Only experts like "ago" can answer that.

Looking for a solution. Thanks everyone.

---

### Post by iamclueless on 2008-04-18
@ Rajan Varadarajan

I've been digging and its looking promising.  looking a grub anyway... we more or less want the same i think

best two links i found

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
[http://64.124.13.3/hacks/USB_Boot_using_GRUB.html](http://64.124.13.3/hacks/USB_Boot_using_GRUB.html)

i can confirm that grub can find the built in USB 1.1 device.  And it can also find the 2 USB 2.0 on the PCI card.  Now its time to get a big pen drive and start playing.

From my limited understanding you can set up the grub to look for a USB boot... and then it will then boot whatever bootable device you have.

The goal at the end of this is having a booting mini hard drive (probably WindowsXP... haha dont ask)

help or further guidance for the experts would be appreciated.

---

### Post by iamclueless on 2008-04-19
Question: I am going to wait for the full release of 8.04. But, in view of your comment, I am envisioning a scenario like this -
1. Install Wubi in one of the folders.
2. Running Wubi establishes the option in the boot menu to go between XP and ubuntu.
3. Do a full install of ubuntu on the external passport hard drive; grub is going to be installed on the main hard drive so if I select ubuntu in the boot menu, grub can be run from the hard drive and the full ubuntu can be loaded from the passport drive.
<the major question is: will installing grub wreck my XP? even if there is a remote possibility, I don't want to risk it:-)>
4. Install other ubuntu apps as needed on the passport drive.

Will this scenario work? Thanks again.[/QUOTE]

hmm im starting to think you (we) can do this.  In your situation it would probably start from Grub ->>>> choice to either a hardrive boot or do a USB boot.  USB boot gets you to your full Ubuntu and the hard drive gets you to Wubi and the choice between windows and the wubied ubuntu.

let me know how you progress

---

### Post by Rajan Varadarajan on 2008-05-02
> **iamclueless said:**
> Question: I am going to wait for the full release of 8.04. But, in view of your comment, I am envisioning a scenario like this -
1. Install Wubi in one of the folders.
2. Running Wubi establishes the option in the boot menu to go between XP and ubuntu.
3. Do a full install of ubuntu on the external passport hard drive; grub is going to be installed on the main hard drive so if I select ubuntu in the boot menu, grub can be run from the hard drive and the full ubuntu can be loaded from the passport drive.
<the major question is: will installing grub wreck my XP? even if there is a remote possibility, I don't want to risk it:-)>
4. Install other ubuntu apps as needed on the passport drive.

Will this scenario work? Thanks again.

hmm im starting to think you (we) can do this.  In your situation it would probably start from Grub ->>>> choice to either a hardrive boot or do a USB boot.  USB boot gets you to your full Ubuntu and the hard drive gets you to Wubi and the choice between windows and the wubied ubuntu.

let me know how you progress[/QUOTE]

Well, this experiment has turned into a mini-disaster. I downloaded 8.0.4, created an image and booted with it. Then I selected install and ubuntu took its own time. I selected my Passport external drive as the target drive to install. At the grub install screen, I clicked the Advanced button and asked ubuntu to install grub on the usb hard drive. Unlike 7.10, this time the install went through and didn't crash. Then I tried to boot - NOTE that I had already installed Wubi and selected the ubuntu boot option from the boot menu. But it didn't recognize the usb installation at all and displayed a message saying a bunch of files missing (grub4dos, etc.).

I switched back to Win XP but much to my horror, the usb drive is no longer recognized. I think the ubuntu install completely formatted my usb passport drive in ext3 format and so windows cannot see it any more. It was originally in FAT32 format. How do I get that drive back? or my $100 down the drain? Can I boot with 8.0.4 CD and re-format the drive as FAT 32?

Thanks much in advance for any help.

---

### Post by ago on 2008-05-02
I will provide instructions to do so in the future. Remind me in a few weeks too busy right now :P

---

### Post by Rajan Varadarajan on 2008-05-02
> **ago said:**
> I will provide instructions to do so in the future. Remind me in a few weeks too busy right now :P

Ago, thanks much in advance. Fortunately, before I embarked on this experiment, I made sure that I didn't have any data on the passport drive. So I didn't lose any content; just the experimentation time which I consider as a learning exercise. Thanks agin.

---

### Post by iamclueless on 2008-05-02
> **Rajan Varadarajan said:**
> hmm im starting to think you (we) can do this.  In your situation it would probably start from Grub ->>>> choice to either a hardrive boot or do a USB boot.  USB boot gets you to your full Ubuntu and the hard drive gets you to Wubi and the choice between windows and the wubied ubuntu.

let me know how you progress

Well, this experiment has turned into a mini-disaster. I downloaded 8.0.4, created an image and booted with it. Then I selected install and ubuntu took its own time. I selected my Passport external drive as the target drive to install. At the grub install screen, I clicked the Advanced button and asked ubuntu to install grub on the usb hard drive. Unlike 7.10, this time the install went through and didn't crash. Then I tried to boot - NOTE that I had already installed Wubi and selected the ubuntu boot option from the boot menu. But it didn't recognize the usb installation at all and displayed a message saying a bunch of files missing (grub4dos, etc.).

I switched back to Win XP but much to my horror, the usb drive is no longer recognized. I think the ubuntu install completely formatted my usb passport drive in ext3 format and so windows cannot see it any more. It was originally in FAT32 format. How do I get that drive back? or my $100 down the drain? Can I boot with 8.0.4 CD and re-format the drive as FAT 32?

Thanks much in advance for any help.[/QUOTE]

you are fine...

boot up with a live cd that has gparted in it (not sure if hardy has it... im sure it does).  have your external usb drive attached

go into gparted and see what file format the external drive is.  fix it back to fat if you need to.

---

### Post by ago on 2008-05-02
You should be able to format that from Windows to. Of course you can format as fat32 also from within Linux.

---

### Post by Rajan Varadarajan on 2008-05-03
> clueless said "you are fine...

boot up with a live cd that has gparted in it (not sure if hardy has it... im sure it does). have your external usb drive attached

go into gparted and see what file format the external drive is. fix it back to fat if you need to."

Thanks much. I have an old 1.5GHz Pentium 4 e-machines desktop running ubuntu; just updated to 8.0.4 (took about overnight but went fine). Installed gparted and restored my passport drive and WinXP sees it fine.

Will remind ago in a couple of weeks about the usb install of 8.0.4 again. Gracias, again.

---

### Post by Rajan Varadarajan on 2008-05-17
> **ago said:**
> I will provide instructions to do so in the future. Remind me in a few weeks too busy right now :P

Ago, just a humble reminder as to whether you have found any solutions to USB booting of 8.0.4 on laptops without the USB boot option? Thanks.

Ago, I ran into this article today.
<Quote>[http://www.linux.com/feature/134670](http://www.linux.com/feature/134670)
Comparing Linux USB flash disk distros
By Gary Sims on May 22, 2008 (9:00:00 AM)
Ubuntu
Ubuntu doesn't come with an easy way to install it to a USB flash disk, but the Pendrivelinux Web site has an article about how you can shoehorn it onto a flash device. The fairly complicated procedure requires 21 steps. You will need to use command-line tools like syslinux, mkfs.ext2, and apt-get, so the process isn't for the novice. However, if these commands don't frighten you, then it's worth trying.

Once it's installed, you have a normal full Ubuntu system. The OS takes 750MB of your flash disk; whatever is remaining is for your files and documents. Because it's Ubuntu, you get a whole host of software, including the latest versions of GNOME, OpenOffice.Org, Firefox, and so on. 

There is one problem with Ubuntu on flash, and it isn't really a technical one. Whenever I used it, I felt uneasy because I knew Ubuntu wasn't designed to run from a flash drive. After a time, my fears were realized. One time, for no apparent reason, the disk would no longer boot, and I was forced to reinstall the operating system. After the reinstall, all seemed fine, but later GNOME had problems starting, and I kept getting an error message about some files being unwritable. At that point, I gave up.

This is not a bad reflection on Ubuntu, but rather a warning about the dangers of trying to force complicated software to reside where it wasn't designed to be.</Quote>

It looks like the same thing I have been complaining about. The procedure is too long and too tricky, which is where I thought Wubi would do the job.

Anyway, thanks again for your suggestions.

---

### Post by Rajan Varadarajan on 2008-06-16
I have been looking around and tinkering with a few ideas but I have not been able to install 8.0.4 ubuntu on a USB hard drive (western digital 250 gb passport).

Ago, any suggestions will be appreciated.

To recap, I don't have a BIOS that allows USB boot.

Thanks much.

---

### Post by ago on 2008-06-17
If your bios does not support usb booting then you need to place the relevant bootloader files (grub4dos) on the hard disk

---

### Post by Guspaz on 2008-06-18
I actually ran into the exact same situation yesterday. My laptop has a 160GB main drive (not much space left), and a 1TB external USB drive (lots of space left).

First thing I tried to do was install with Wubi to my external drive. That seemed to go OK, but when I rebooted, and selected Kubuntu in the Vista bootloader, it complained that it couldn't find wubi's .mbr file. It seems that grub supports booting off USB devices, but Vista's bootloader doesn't. My laptop's BIOS does support loading off a USB disk, but Wubi will go through your main bootloader, which is on your main drive.

My solution:

1) Install Wubi to my USB disk.
2) When Wubi prompts to reboot, copy the winboot directory to your C drive (including the hierarchy, so you have c:\ubuntu\winboot)
3) Modify the Windows boot record to load the MBR file off your C drive. Under Vista, I used the "bcdedit" commandline app. Under XP, I guess you'd edit the boot.ini file.
4) Reboot into Ubuntu. During the boot process, when grub tells you to hit "escape" to see the menu, hit escape and start the installer up in verbose mode instead. If you don't it might drop you to an initramfs busybox prompt.

That was it. The second install process with verbose mode on worked, and eventually I was left with a completely working Wubi installation. The MBR stuff is on my main disk, and everything else is on my 1TB USB disk.

EDIT: I wanted to clarify step 3, as it sounds more complicated than it is. Under Vista:

1) Open a command prompt
2) Run "bcdedit"
3) Look for Wubi's entry. It should look like this:

```
Real-mode Boot Sector
---------------------
identifier              {d63f4fae-3cf6-11dd-b70d-00188ba28f6c}
device                  partition=H:
path                    \ubuntu\winboot\wubildr.mbr
description             Kubuntu
```

4) Note that H is my USB hard drive. I now run the command: "bcdedit /set {d63f4fae-3cf6-11dd-b70d-00188ba28f6c} device partition=C:"

That's it. Done. Make sure to use the identifier from your own drive, as it won't be the same as mine. You may want to run bcdedit once again to make sure the device is really changed, but it should have given you a confirmation anyhow.

---

### Post by geeham on 2010-03-19
Hi,

sorry to drag up such an old post.

I just wanted to ask if the instructions above would still be valid for Ubuntu 9.10 & Windows 7 as this is how i would like to set this up.

also where you say your usb hdd was H: my setup is a sony laptop with card reader which as far as i am aware is not available until after windows has booted, so theoretically my only drives would be c: d: (cdrom) and e: for usb hdd. - However once windows has started my drive is a differnt letter.

Hope that makes sense, and thanks in avance for any help you can give.

---

