---
title: "Booting from grub rescue&gt; with no access to BIOS or boot menu"
date: 2014-11-16
forum: General Help
---

### Post by sarah14 on 2014-11-16
Hi Everyone,

I really messed up and would greatly appreciate if anyone could help me. Please. 

I have a Lenovo Ideapad U410. I had the a dual boot system set up with Ubuntu and Windows 8. For some stupid reason, I thought it would be a great idea to delete my Linux partitions using Windows 8 disk manager. Grub was my default boot manager and was deleted in the process :(. 

I've spent a great amount of time reading several threads and forums but to no luck so I thought I'd start a new thread. Please help me.
My initial idea was to just boot from my bootable Ubuntu from by USB. However, I don't have access to the BIOS or the boot menu to change the boot order. I've tried a vast amount of combinations on system startup to try and get into the BIOS but nothing works. (F2, Fn+F2, F12, you name it). However, there is also another button on the side of my laptop which launches a Novo Button Menu which presents me with options to select the BIOS and Boot Menu, but it still goes to the grub rescue> terminal when I try to select one of those options.

Executing the ls command gets me the following output:
(hd0)  (hd1)  (hd2)  (hd2,gpt8)  (hd2,gpt7)  (hd2,gpt6)  (hd2,gpt5)  (hd2,gpt4) (hd2,gpt3)  (hd2,gpt2)  (hd2,gpt1)

The most relevant thread I could find was this one:
[http://ubuntuforums.org/showthread.php?t=2207871](http://ubuntuforums.org/showthread.php?t=2207871)

I tried andrew94's solution of booting into Ubuntu from another PC and installing a copy on a USB stick. However, when I plug in the USB to my non bootable laptop and try to run:

ls (hd0)/

The output says error: unknown filesystem
I assume hd0 is my USB stick as the light on my USB flashes when I execute ls (hd0)/.

I'm open to any thought and/or ideas. How can I get into my Windows 8 or a Ubuntu from my USB from grub rescue> so that I can fix the MBR.

Thank you so much in advance.

---

### Post by oldfred on 2014-11-16
You are showing drive is gpt partitioned, so then Windows must be installed in UEFI boot mode. Then all you have to do is go into UEFI/BIOS and reset it to boot Windows.

And there has to be a way to get into UEFI or a one-time boot key like f12 or f10. 

Some systems will get into otherwise locked up system, after a full power down. If laptop also remove battery. Hold power switch to remove residual power for a minute and then reboot using correct key to get into UEFI.

 Lenovo U410 How to 
[http://ubuntuforums.org/showthread.php?t=2190980](http://ubuntuforums.org/showthread.php?t=2190980)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.

---

