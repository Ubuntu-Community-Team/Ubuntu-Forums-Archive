---
title: "GNU GRUB on startup, no CD"
date: 2013-03-27
forum: General Help
---

### Post by allegroconcerto on 2013-03-27
I got the same problem and I don't seem to be able to resolve this because my CD ROM is dysfunctional so I cannot do a wipe and reinstall. I put Ubuntu using PLOP manager when I had Windows XP... I then overwrite the Windows XP with Ubuntu.

None of the above solution would work because I cannot get pass GRUB GNU screen.

Is there anyway out of this?

---

### Post by oldfred on 2013-03-27
Moved to your own thread.

You really have to have a way to boot externally, either CD or flash drive to make repairs.

If you get a grub rescue prompt, you should be able to manually boot.

       Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

If computer does not boot from USB, then you need to repair or replace CD drive. Sometimes it may just need cleaning? Or check connections.
      
 How to clean CD lens:
[http://members.iinet.net.au/~herman546/p27.html](http://members.iinet.net.au/~herman546/p27.html)

---

### Post by allegroconcerto on 2013-03-28
Yes I did try the Grub Rescue thread, it does not work and I don't know why mine looks like (hd0) (hd0,msdos5) (hd0,msdos1)...

---

### Post by oldfred on 2013-03-28
They have added msdos to tell it apart from the newer gpt. My gpt drive looks like (hd0), (hd0,gpt1).

Two choices, new CD or maybe you can remove drive, and plug into another system as an external or even internal drive. Then you can make repairs.

---

### Post by allegroconcerto on 2013-04-01
Okay, I bought a replacement CD drive, what is the next step? I tried to wipe out Ubuntu altogether with my original Windows XP recovery CD, but I got Error #1826 Free space not found

---

### Post by fantab on 2013-04-01
Yes Windows does NOT work on ext4/Linux partitions. Download and burn a fresh Ubuntu.iso (burn at the lowest possible speed), if you don't already have Ubuntu LiveCD/DVD. Boot with it and opt for "Try Ubuntu", once the Desktop is ready Back Up and rescue any DATA that you want to. Then open and run GPARTED, using which you can repartition your HDD accordingly.

From the desktop icon "Install ubuntu" install your Ubuntu and at the appropriate screen choose "Something Else" option to manually set your install target partition on HDD. [More Info Here]("http://www.ubuntu.com/download/help/install-desktop-long-term-support"). Or you can just Install ubuntu with default install method.

---

### Post by allegroconcerto on 2013-04-01
Thanks for the above reply, I will try to get a LiveCD with [COLOR=#333333]12.04.2 LTS, I am guessing it does not matter even though I installed 12.10 originally?

The part I am unsure about is this: "[/COLOR][COLOR=#000000]Then open and run GPARTED, using which you can repartition your HDD accordingly", is there a step by step guide somewhere for reinstalling Windows XP?


My Windows XP CD is just a recovery disk rather than a full installation CD, I don't know if that would change the situation somewhat?


Sorry about all these questions...
[/COLOR][COLOR=#333333][FONT=arial]



[/FONT][/COLOR]

---

### Post by fantab on 2013-04-01
So you want to install Windows XP as well, and dual-boot?

If that is the case, then, if you have a Windows Key for XP/Vista/7/8, you can download the version the key is for, say, Windows Vista Home Premium and use the Key you have to activate it.

If you are going to dual boot then I suggest that you Install Windows First and on the FIRST PARTITION of your HDD. CREATE & FORMAT partitions for Windows with Windows Install Disc ONLY.

After that you can install Ubuntu. But first tell us CLEARLY how you want to set up your computer, Ubuntu only or Dual boot Windows and Ubuntu or just Windows. Only then we'll be able to guide you in the right direction.

---

### Post by oldfred on 2013-04-01
Gparted is on Ubuntu live installer or you can download a a liveCD.

 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

      
 [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

Windows only installs to a NTFS formatted primary partition (sda1 thru sda4) with the boot flag. 
Normally a recovery install, just erases entire drive and reinstalls system to as purchased. If you have any data you want to save, back that up first. To use that You probably just have to totally erase drive. You should also be able to do that from Window command line, if recovery will also boot into the repair console.

If you only have an XP key that is all you can install, unless you purchase the full install media.

---

### Post by Slim Odds on 2013-04-01
> **fantab said:**
> Yes Windows does NOT work on ext4/Linux partitions. Download and burn a fresh Ubuntu.iso [COLOR=#ff0000](burn at the lowest possible speed),[/COLOR] if you don't already have Ubuntu LiveCD/DVD. Boot with it and opt for "Try Ubuntu", once the Desktop is ready Back Up and rescue any DATA that you want to. Then open and run GPARTED, using which you can repartition your HDD accordingly.

From the desktop icon "Install ubuntu" install your Ubuntu and at the appropriate screen choose "Something Else" option to manually set your install target partition on HDD. [More Info Here]("http://www.ubuntu.com/download/help/install-desktop-long-term-support"). Or you can just Install ubuntu with default install method.
Please stop perpetuating this long worn out myth. Modern CD burners will actually produce a worst result by doing this.

[http://www.digitalfaq.com/guides/media/dvd-media-concepts.htm](http://www.digitalfaq.com/guides/media/dvd-media-concepts.htm)

[http://club.myce.com/f33/slow-write-speeds-modern-drives-modern-media-no-good-247643/](http://club.myce.com/f33/slow-write-speeds-modern-drives-modern-media-no-good-247643/)

It you're concerned about getting the disc burnt correctly, turn on write verification. Any decent CD writing software has that.

---

### Post by fantab on 2013-04-01
> **Slim Odds said:**
> Please stop perpetuating this long worn out myth. Modern CD burners will actually produce a worst result by doing this.

I have a relatively new CD/DVD burner (2010-11) and **at times** it does create problems if I burn, especially, OS and other Software at the burner's optimal speed, in spite of enabling 'verification'. I have also seen this happening on "Newer" Burners. "Bad Burn" at optimal speed is a possibility even with the best of Burners out there. Its not yet, a myth; at least NOT in my personal experience. Also until now I haven't seen any adverse effects by burning at slowest possible speeds.
Burning at the 'slowest possible speed' is the pre-caution I take when burning an OS.

However, I haven't faced any issues with Data burning at Max. speeds. 

Thanks for the Links.

---

### Post by oldfred on 2013-04-01
I think years ago I had similar experiences as fantab. I made a lot of coasters. But now with flash drives, for me the entire issue is moot. I converted to flash drive installs several years ago. But now with multiple hard drives just install from one hard drive to another. Quicker, easier and more reliable.

With the Ubuntu install now larger and flash drives dropping in prices, flash drive should be first choice to use to install. Only very old systems that probably should have Lubuntu may not boot from a flash drive anyway.

---

### Post by Slim Odds on 2013-04-01
> **fantab said:**
> I have a relatively new CD/DVD burner (2010-11) and **at times** it does create problems if I burn, especially, OS and other Software at the burner's optimal speed, in spite of enabling 'verification'. I have also seen this happening on "Newer" Burners. "Bad Burn" at optimal speed is a possibility even with the best of Burners out there. Its not yet, a myth; at least NOT in my personal experience. Also until now I haven't seen any adverse effects by burning at slowest possible speeds.
Burning at the 'slowest possible speed' is the pre-caution I take when burning an OS.

However, I haven't faced any issues with Data burning at Max. speeds. 

Thanks for the Links.
You're welcome for the links.

FYI, all CD's & DVD's are just data, no matter what that data really is.

Bottom line is that there is never a good reason to burn at the "lowest possible speed". At "not the highest speed", maybe. If anything, burn at half the highest speed, that will give better results than the "lowest possible speed".

---

### Post by Slim Odds on 2013-04-01
> **oldfred said:**
> I think years ago I had similar experiences as fantab. I made a lot of coasters. But now with flash drives, for me the entire issue is moot. I converted to flash drive installs several years ago. But now with multiple hard drives just install from one hard drive to another. Quicker, easier and more reliable.

With the Ubuntu install now larger and flash drives dropping in prices, flash drive should be first choice to use to install. Only very old systems that probably should have Lubuntu may not boot from a flash drive anyway.
I agree; I much prefer to boot from USB whenever possible.

---

### Post by allegroconcerto on 2013-04-01
At the moment I just want to install Windows XP, but I said before I only got a recovery disc that comes with the laptop, so I don't think I can create and format partitions at all?

I think once I got Windows, it is relatively easy to get Ubuntu, I might give this a go again, but so far, it has been nothing but nightmares for me....

---

### Post by allegroconcerto on 2013-04-02
Actually, I created the boot CD using Roxio, downloaded ubuntu-12.04.2-desktop-i386.iso and burn this as image. The CD however, was excruciatingly slow. What is going on here?
 
I managed to get as far as Loading bootlogo... should I just wait or try to create from DVD? That means another trip to the shops... I think Ubuntu is a good training for patience...

---

### Post by fantab on 2013-04-02
The initial boot is 'slow' from DVD (compared to USB). I suggest you wait until the DVD boots. If you select 'Try Ubuntu' you will have to wait another few minutes. Sometimes it does take the entire installation process a good hour to finish, but once the installation is finished Ubuntu will be as fast as it should be. 

Stop wasting DVDs if you have access to USB flash/pen drive. If you have read the posts by **oldfred** and **Slim Odds** you will understand why. I have stopped using DVD/CDs in favor of USB Drives some time back.

---

### Post by allegroconcerto on 2013-04-02
I cannot boot at all from USB, that was why I had to get a replacement CD/DVD drive. When I say its slow, it is slow in the sense there is almost no progress whatsoever, it takes forever to display the contents in the CD from the other laptop which I used to create the boot CD/DVD. In fact, the laptop just freezes whenever I asked my other laptop to display the content.

The process simply stopped at loading boot logo, there was no progress at all after 30 minutes, I am going to ask my friend to see if he could create a working DVD as I don't know if this to do with Roxio software (which is the only software available as I do not have administrator right on this laptop and there was no option of choosing write speed).

There seems to be a lot of problems with Ubuntu, so what is the best way to remove this completely and get Windows XP back?

---

### Post by oldfred on 2013-04-02
Are you trying full Ubuntu on a very old system. Ubuntu now is a full system that requires fairly new systems or at least more memory. If an older system Lubuntu often is a better choice.
But my systems are 6 years old, boot from flash and run Ubuntu with fallback just fine.

You should be able from XP also erase the entire drive, even though it cannot really see the Linux partitions. 
 XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

---

### Post by allegroconcerto on 2013-04-02
> **oldfred said:**
> 
You should be able from XP also erase the entire drive, even though it cannot really see the Linux partitions. 


[SIZE=3][FONT=arial]No I cannot, because as I said before, I only have a Recovery DVD that comes with the laptop, I don't have any options whatsoever that looks like "[COLOR=#232323]Repair a Windows XP Installation" as described there. 

I am thinking perhaps I can at least try to get Ubuntu back, and then go from there. 


[/COLOR][/FONT][/SIZE]

---

### Post by allegroconcerto on 2013-04-02
Also, I don't think memory is an issue, because my work laptop cannot read the CD created by Roxio either. 

What is the next step even if I can get CD/DVD to work? Create a partition and then...? Or should I reinstall Ubuntu and then somehow try to get XP back?

---

### Post by fantab on 2013-04-02
> **allegroconcerto said:**
> [SIZE=3][FONT=arial]No I cannot, because as I said before, I only have a Recovery DVD that comes with the laptop, I don't have any options whatsoever that looks like "[COLOR=#232323]Repair a Windows XP Installation" as described there. 

I am thinking perhaps I can at least try to get Ubuntu back, and then go from there. [/COLOR][/FONT][/SIZE]

Then why don't you download a full XP SP3 and burn it or Vista or Win7? If you do have an Activation Key for any Windows you can download, install that version and activate it. Try using a different Burner. 

Yes you can install Ubuntu. Just don't install it on /dev/sda1 , ie the first partition, if you want to install Windows later. Remember, if you install Windows after Linux you will have to "fix" Grub later.

---

### Post by allegroconcerto on 2013-04-03
Okay thanks.

I finally got a liveCD working, I think its to do with a faulty burner.

I was thinking, can I use Gparted to delete all partitions and reformat my drive to NFTS and try to use Windows Recovery CD to reinstall everything? Would this work?

I had a look at my partition and it looks like the following:

/dev/sda1
File system: ext2
Size: 243.00 MiB
Used: 79.03 MiB
Flag:boot

/dev/sda2
File system: extended
Size 92.73 GiB

/dev/sda5 (with a red exclaimation mark)
File system: crpyt-luks
Size 92.73 GiB

Not exactly what to do from here, is there a tutorial somewhere? I think the best situation is to have a dual boot, but it seems the easiest to get Windows XP and then install Ubuntu?

(The only reason I am using Windows is because of Microsoft Office and Endnote etc... because my collaborators use them...)

---

### Post by fantab on 2013-04-03
Delete all partitions with GParted (DON'T create any partitions) and try that "recovery disc".

---

### Post by allegroconcerto on 2013-04-03
Thanks to all of you who replied. I have solved the problem now.

This is just provided for the benefit of others who may have the same problem.

My problem originally was I could not boot into an operating system and instead got stuck at GNU GRUB screen. At the time I don't have a working CD/DVD drive and I cannot boot from USB.

After mucking about various tutorials on GNU GRUB and getting nowhere, I decided to see if I could replace my CD/DVD drive, it was actually not that hard to take it out, the hard part was to find a replacement optical drive that would work. It took me about half of day walking around various computer shops and took me some time to replace the face panel of my replacement CD/DVD drive so they would fit into my laptop.

I then proceeded to create a Live CD with Ubuntu 12.04 LT, after some false starts, I finally got a working CD. Booting from Live CD with Ubuntu I then selected Try Ubuntu.

I then went to Dash and type GParted to start the program, I deleted all the partitions there and rebooted with my Windows Recovery CD. This time, it worked.

I was unable to get back to Windows XP however after the first installation, I kept on getting back to the first boot screen. So I went back to booting with Ubuntu LiveCD and I noticed Windows XP was installed on /dev/sda1. So I thought, well, maybe I would just install Ubuntu 12.04, at least I would have a working operating system. 

After this installation, I rebooted without Live CD and I decided to try Windows XP to see if it would work... As if by some magic, this time I could get into Windows without any issues. 

So I ended up with both XP and Ubuntu on my system now. And for now, I am happy.

This wasn't an easy journey for me though, but I did make it through eventually...

---

