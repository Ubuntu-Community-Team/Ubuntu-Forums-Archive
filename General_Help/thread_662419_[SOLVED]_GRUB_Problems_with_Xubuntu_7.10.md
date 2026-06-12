---
title: "[SOLVED] GRUB Problems with Xubuntu 7.10"
date: 2008-01-08
forum: General Help
---

### Post by jeremyj on 2008-01-08
Hi, I just installed Xubuntu 7.10 Gusty Gibbon this evening, and all went well with the installation it seemed.  However, when I restarted my laptop, nothing loaded except a black screen with the word "GRUB" on it and a blinking cursor beside it like it wanted me to type in something.  Nothing works to get it to load.  It just sits there.  Any ideas?  Please help.  Thanks.

---

### Post by ModelM on 2008-01-08
Is this a Linux-only machine or dual-boot?

---

### Post by jeremyj on 2008-01-08
It's Linux only.  I wanted to have my whole hard drive run Xubuntu because it's an old laptop from a few years ago, and Windows barely functions on it.

---

### Post by jeremyj on 2008-01-09
I probably should have put my laptop's specs here, so here you go if it helps.  Although, I copied this from Amazon.com and am not sure if these are completely correct.  The photo of the laptop was not very detailed (at an angle where most people can't see much detail like the keyboard layout), but it looked very similar if not the same model.  I searched for my exact brand and model and got these results:

    * Hardware Platform: PC
    * Processor: 1.1 GHz Intel Celeron
    * System Bus Speed: 100
    * Number of Processors: 1
    * RAM: 256 MB
    * RAM Type: SDRAM
    * L2 Cache: 128 KB

Hard Drive

    * Size: 20 GB
    * Manufacturer: Portable
    * Type: IDE

Graphics and Display

    * Graphics Card: Trident CyberAladdin
    * Graphics RAM: 16 MB
    * LCD Native Resolution: 1024-by-768

Also, I should have mentioned that it looks like my BIOS is booting, because the Toshiba logo displays, and I can press F8 or F12 and get those respective screens.  However, I am not getting any Xubuntu splash screen, GUI, or loading bar at all.  It goes straight from the Toshiba BIOS logo to a black screen that says "GRUB" with a blinking underscore cursor.  Thanks for the help.

---

### Post by logos34 on 2008-01-09
Pop in the xubuntu install cd and select 'boot from first hard disk'.  Or try Super Grub Disk.

see 'grub errors' on [this page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by logos34 on 2008-01-09
you could also try [reinstalling grub to mbr.]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by jeremyj on 2008-01-09
> **logos34 said:**
> Pop in the xubuntu install cd and select 'boot from first hard disk'.  Or try Super Grub Disk.

see 'grub errors' on [this page]("http://users.bigpond.net.au/hermanzone/p15.htm")

I've tried using the install disc and selecting "Boot from first hard disk," but it just loads the same black screen with the word "GRUB" and the blinking underscore cursor.

I also tried a complete reinstall of Xubuntu with it connected to my wired broadband internet connection in the hopes that an update was available that would fix the problem. (Or if something happened during the first install that could be fixed with a reinstall.)

What exactly is the Super Grub Disk?

How do I reinstall the GRUB to mbr?  And what is mbr?  (I apologize for my incompetence if that's a stupid question.  Haha.)

Also, no keys seem to work while the blinking underscore cursor is onscreen.  I verified that the keyboard settings would work when I used the small text box in the keyboard settings during the install, so I'm sure that's not a problem.  I used to have Ubuntu 6.06 on this laptop, but since it's an older model, it was slowing down some and crashing (probably due to not having enough memory), so Ubuntu or Xubuntu should definitely be compatible with my laptop.

And in reference back to what I was saying about no keys seem to work, is there a key combination I should try?  No single keys work, I've tried Ctrl + Alt + F1, but that didn't do anything.  Thanks again for the help in advance.

---

### Post by artinla on 2008-01-09
Not sure why you are having the trouble, there are several stages to grub and you seem to be failing just as grub looks for a bootable partition.

This page explains the MBR:

[http://www.pcguide.com/ref/hdd/file/structMBR-c.html](http://www.pcguide.com/ref/hdd/file/structMBR-c.html)

If your system booted from the livecd, it should boot equally well from the HD install if your hard drive is good.

Here is an excerpt from the "Grub" troubleshooting manual that describes what should be happening when your system fails:

"14.1 Errors reported by the Stage 1

The general way that the Stage 1 handles errors is to print an error string and then halt. Pressing <CTRL>-<ALT>-<DEL> will reboot.

The following is a comprehensive list of error messages for the Stage 1:

Hard Disk Error
    The stage2 or stage1.5 is being read from a hard disk, and the attempt to determine the size and geometry of the hard disk failed.
Floppy Error
    The stage2 or stage1.5 is being read from a floppy disk, and the attempt to determine the size and geometry of the floppy disk failed. It's listed as a separate error since the probe sequence is different than for hard disks.
Read Error
    A disk read error happened while trying to read the stage2 or stage1.5.
Geom Error
    The location of the stage2 or stage1.5 is not in the portion of the disk supported directly by the BIOS read calls. This could occur because the BIOS translated geometry has been changed by the user or the disk is moved to another machine or controller after installation, or GRUB was not installed using itself (if it was, the Stage 2 version of this error would have been seen during that process and it would not have completed the install). "

If it were me, I would try reinstalling Ubuntu before digging too deep into grub.  It isn't usually an easy thing for new users to troubleshoot.

---

### Post by logos34 on 2008-01-09
> **artinla said:**
> If it were me, I would try reinstalling Ubuntu before digging too deep into grub.  It isn't usually an easy thing for new users to troubleshoot.

Yes, but just reinstalling won't do any good unless he does something different.

jeremyj,

If you have floppy drive you could reinstall and tell it to put grub on the floppy instead.  ('Ready to install' screen>hit 'Advanced' button lower right>replace (hd0) with **(fd0)**.) If it allows you to boot into ubuntu then you know the problem is isolated to the hard disk mbr.  

Just for good measure you could also install grub to the root partition before you exit the installation (choose 'continue using live cd').

**sudo grub-install /dev/hda1**  (or sda1, or whatever root it)

---

### Post by jeremyj on 2008-01-09
> **artinla said:**
> Not sure why you are having the trouble, there are several stages to grub and you seem to be failing just as grub looks for a bootable partition.

This page explains the MBR:

[http://www.pcguide.com/ref/hdd/file/structMBR-c.html](http://www.pcguide.com/ref/hdd/file/structMBR-c.html)

If your system booted from the livecd, it should boot equally well from the HD install if your hard drive is good.

Here is an excerpt from the "Grub" troubleshooting manual that describes what should be happening when your system fails:

"14.1 Errors reported by the Stage 1

The general way that the Stage 1 handles errors is to print an error string and then halt. Pressing <CTRL>-<ALT>-<DEL> will reboot.

The following is a comprehensive list of error messages for the Stage 1:

Hard Disk Error
    The stage2 or stage1.5 is being read from a hard disk, and the attempt to determine the size and geometry of the hard disk failed.
Floppy Error
    The stage2 or stage1.5 is being read from a floppy disk, and the attempt to determine the size and geometry of the floppy disk failed. It's listed as a separate error since the probe sequence is different than for hard disks.
Read Error
    A disk read error happened while trying to read the stage2 or stage1.5.
Geom Error
    The location of the stage2 or stage1.5 is not in the portion of the disk supported directly by the BIOS read calls. This could occur because the BIOS translated geometry has been changed by the user or the disk is moved to another machine or controller after installation, or GRUB was not installed using itself (if it was, the Stage 2 version of this error would have been seen during that process and it would not have completed the install). "

If it were me, I would try reinstalling Ubuntu before digging too deep into grub.  It isn't usually an easy thing for new users to troubleshoot.

I'm not sure if Ubuntu will run well on my laptop though.  I used Ubuntu 6.06 for a few months, but it kept slowing down and crashing.  I assumed it was because of a memory shortage.  Xubuntu looked like it would work best because Ubuntu promotes it as an OS that runs extremely well on older PC's.

I'm not receiving any error messages either.  Just the word "GRUB" and the blinking cursor.  I can, however, use Ctrl + Alt + Delete on the screen where the word "GRUB" and the cursor are to reboot the system, but it just repeats the whole process of showing the Toshiba BIOS logo, and going straight back to the black screen with the cursor and the word "GRUB."

I know the hard drive is good, so even though GRUB is failing to find a bootable HD, a bad HD can't be the case.  I had a slightly older version of Linux Fedora (a college textook edition) running well on this laptop right before I tried installing Xubuntu.

As for the MBR, I don't see one when it boots up.  Presumably because this is a Xubuntu only laptop.  No other OS is installed.  I wiped the HD clean of Fedora when switching to Xubuntu.

---

### Post by jeremyj on 2008-01-10
I tried once again to reinstall Xubuntu, only this time I went to the Advanced options near the end of the installation's setup process, and changed the code(?) for where Xubuntu should be installed from hd0 to hd1, however, it didn't work.  I had no clue if that would work or not, but I thought I'd give it a try.  At the very end of the installation process, once it got to about 95% done, I received an error message stating:  "Executing 'grub-install(hd1)' failed.  This is a fatal error."

logos34, I will try your instructions later tomorrow (Jan. 10th) about using the floppy drive.

---

### Post by mactece on 2008-01-10
I'm not an expert but have thrashed around in this area before so here's the benefit of my "experience":

Burn a supergrub disk. Supergrub should find all teh bits and pieces and fix the grub bootup sequence. You'll be presented with a text based interface and when I used it I just kept following the selection that sounded most likely. This is not an intuitive system but it sounds like you have no data to lose and the worst that can happen is that you need to reinstall. Follow the instructions while keeping your fingers crossed and with a bit of luck it will straighten everything out. 

If this fails then:

Can you boot from a floppy and read the hard drive - good to know if its still there!

Working with the hard drive from a Ubuntu floppy is difficult. It's easier with PClinux or Knoppix. I prefer the PCLinux which is very intuitive (but for a full os I think Ubuntu wins overall). If you can get this up and going then you should be able to find your "menu.lst" file in <boot<grub on your hard drive. Then you can find out if that's correct and do some sense checking.

Try installing PCLinux or another OS. If this works you'll know the bug is with Ubuntu's installer.

good luck!

---

### Post by jeremyj on 2008-01-12
Thanks to all who offered advice on this.  Xubuntu never would install, and once I thought about it a little more, I figured trying the floppy disk trick would be too much of a hassle.  So, I installed Ubuntu (not Xubuntu) 7.04 and tried to upgrade to 7.10.  My laptop gave out on me towards the end of the upgrade install, so I downloaded the 7.10 OS from Ubuntu's site, burned in to a CD and installed from there.  It works perfectly now (and I'm praying I have no more problems with it or my laptop [-o< ), and I'm typing this from my Ubuntu 7.10 laptop!

Now all I need to do is install Amarok like I once had on my 6.06 install, and any DVD Player like VLC so I can watch my movies and listen to my music once more.  I've done that before, so I don't think I'll need help on installing those.

However, does anyone know of a good wireless internet card that can run with Ubuntu?  Last time a checked (early last year) my Linksys Wireless-B Notebook Adapter 802.11b wasn't compatible with Linux systems.  I might be wrong though, so I'll do some more checking.  I know this last question had nothing to do with the topic of this thread, but I'd appreciate the help very much!  Thanks again to all who helped.  My gratitude cannot be expressed in words alone.  \\:D/

---

### Post by jeremyj on 2008-01-12
> **jeremyj said:**
> However, does anyone know of a good wireless internet card that can run with Ubuntu?  Last time a checked (early last year) my Linksys Wireless-B Notebook Adapter 802.11b wasn't compatible with Linux systems.  I might be wrong though, so I'll do some more checking.  I know this last question had nothing to do with the topic of this thread, but I'd appreciate the help very much!  Thanks again to all who helped.  My gratitude cannot be expressed in words alone.  \\:D/

Instead of keeping track of 2 threads regarding setting up my notebook adapter, I decided to start a new thread in the Networking and Wireless forum:   [http://ubuntuforums.org/showthread.php?t=666015]("http://ubuntuforums.org/showthread.php?t=666015")

Thanks again to all who helped.  And for future readers who might run into this problem, my solution may not be the best answer, but I installed Ubuntu 7.10 instead of Xubuntu 7.10.

---

