---
title: "Uninstalled Ubuntu 13.10 and now reinstalling doesn't work."
date: 2014-04-15
forum: General Help
---

### Post by Mobile_Lawnmower on 2014-04-15
I installed Ubuntu 13.10 in a Dual-Boot setup next to Windows 7 (This installation actually completed and I was able to use Ubuntu normally) but I forgot to defrag my drive before installing it. I proceeded to remove Ubuntu and defragged said drive. I am now trying to reinstall Ubuntu 13.10 using the same DVD as before. I get to the default background but then it stops. During the previous install, I got a "loading" screen followed by the prompt that asks if you want to Try or Install. This time no loading screen or any prompts, just a screen with the default background and nothing else. I have tried booting off of a USB stick and installing Ubuntu 12 (The Long-Term-Support edition) and I get the same exact result. I have done a system restore to a point before I installed Ubuntu the first time and nothing has changed. Any ideas? (BTW, I am trying to install a 64-bit version of Ubuntu)

System Specs:
Windows 7 Home Premium 64-bit
i7-3770k
32GB RAM
GeForce GTX 780Ti SLI'd with
GeForce GTX 680
120GB SSD (Has Windows 7 on it)
2TB HDD (Has my data and is what I previously had Ubuntu on)
Blu-Ray/DVD/CD Reader and Burner

---

### Post by oldfred on 2014-04-15
Welcome to the forums.

With a new system like that, you may be offered to boot in either UEFI or BIOS boot mode. Most Windows 7 systems are BIOS boot. Best to install Ubuntu in same boot mode and if on same drive as Windows it has to be BIOS or drive may be converted from MBR (required for BIOS boot) to gpt (required for UEFI boot).

But you issue probably is nVidia. I have a much older nVidia 9600GT and have to use nomodeset to boot installer and again use nomodeset on first boot or until nVidia driver installed from Ubuntu repository.

       To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place


 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Mobile_Lawnmower on 2014-04-15
Alright, thanks for the speedy reply. I can't try this now as I am away from home, but I will do this and get back to you as soon as I can.
Thanks,

---

### Post by brian-quillen on 2014-04-15
You should never need to defrag Ubuntu (or any Linux Install) [http://www.howtogeek.com/115229/htg-explains-why-linux-doesnt-need-defragmenting/](http://www.howtogeek.com/115229/htg-explains-why-linux-doesnt-need-defragmenting/)

When you try to boot up without the DVD installed, what happens? Are you able to boot into Windows? Does the Grub menu (the boot loader that allows you to choose your OS) appear?

---

### Post by Mobile_Lawnmower on 2014-04-15
I wasn't defragging my Ubuntu installation I was defragging the drive I wanted to install Ubuntu on to give the partition lots of free space. Yes, my Windows boots up normally as it did before my previous (successful) installation. The Grub menu did appear when I had both Windows and Ubuntu on at the same time. When I have the LiveCD in, I get a black screen with a white cursor for a couple of seconds, then I get the screen that lets you go into Advanced Mode if you press a button (I didn't know it did this previously), then I get that same black screen with a flashing white cursor for ~20 seconds, then a gray screen, then just the default Ubuntu background with absolutely nothing else.

---

### Post by brian-quillen on 2014-04-15
> [COLOR=#000000]I wasn't defragging my Ubuntu installation I was defragging the drive I wanted to install Ubuntu on to give the partition lots of free space.[/COLOR]

If you had deleted the partition, there would be no need to defrag it. Deleting it 'deletes' all the data in that space. If you really wanted to make sure that your partition was 'clean' you could 'zero out' the data in that partition, though it isn't really necessary. You'd only really need to do that if you were trying to destroy sensitive data or maleware that was on the deleted partition.

Try what oldfred suggests and post the results here.

---

### Post by Mobile_Lawnmower on 2014-04-17
Sorry for the late reply, I wanted to make sure this would work with Ubuntu 14.04 installation and it did. Thanks

---

