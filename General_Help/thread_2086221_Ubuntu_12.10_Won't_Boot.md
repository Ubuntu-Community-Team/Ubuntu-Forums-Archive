---
title: "Ubuntu 12.10 Won't Boot"
date: 2012-11-20
forum: General Help
---

### Post by David McCoy on 2012-11-20
Hi all, 

I am experiencing the ubuntu 12.10 black screen error so many people are having issues with.  I have an Asus EEE netbook and I believe that the new update is not compatible with my graphics card.  At first the icons went strange then after reboot it just went to black screen.  However now I am getting an error on boot up that states "could not write bytes: Broken pipe" and it is stuck there.  I can't get to console but otherwise I am in a rut.  The big problem is that I am currently serving with the peace corps in Africa so I do not have the internet to download 12.10 fresh and boot from flash.  Does anyone have any suggestions? This is really killing me.  Thanks.  Also sorry if this should have been put in a different thread, my internet is very poor.

---

### Post by NikTh on 2012-11-20
Hi , 
well if you don't have Internet connection , this is a problem. 

I would suggest to re-install Ubuntu 12.04 LTS and not 12.10 for a eeePC Netbook. 
I think 12.10 is a little "heavy" for such netbooks. 
Ubuntu 12.04 has the Unity-2D (ubuntu-2d) environment where is much lighter than compiz (Unity 3D). 

Ubuntu 12.10 uses a new technology , named LLVM pipe . This technology burdens the CPU when GPU is  low specs and not capable to manage the environment , and as you understand the result (when CPU is not strong enough  , eg: netbook) is not good at all. 

Also [Lubuntu 12.10]("http://lubuntu.net/taxonomy/term/226") could be a good advise.

Thanks

---

### Post by David McCoy on 2012-11-21
Hi, 

Thanks for the reply.  Luckily, I can get some internet access through console at a local NGO I was going  to for  internet, the only problem is that it cuts out, then I'm left hanging (so trying to dl the whole 650 mgb os is a nightmare).  Is there anyway through terminal to revert back to 12.04 lts? Or really, is  my only option to boot from flash?

Once again, thanks for your  help.

---

### Post by NikTh on 2012-11-22
> **David McCoy said:**
>   Is there anyway through terminal to revert back to 12.04 lts? Or really, is  my only option to boot from flash?
Hi,

I don't know any way that you can revert back to an older release , except the new install. 

Yes , you have to boot from flash-usb (as netbook has not CD) and install from scratch Ubuntu 12.04. 

Thanks

---

### Post by koebln on 2012-11-22
Di you use 32Bit or 64Bit OS? If you use 64Bit OS, the problem might be an error with the UEFI/GPT Bootloader. Look at 
[http://forum.thinkpads.com/viewtopic.php?f=9&t=107246](http://forum.thinkpads.com/viewtopic.php?f=9&t=107246) 

Renaming the Boot-File to BOOTX64.EFI might be a ThinkPad - specific Solution, but it solved the problem on my PC.

---

### Post by David McCoy on 2012-11-26
Hey Everyone, 

Thanks  for the advice. So, I was able to get a Kenyan  to Download ubuntu 12.04.iso for me and its about 695 mgb, so I think it's  the whole thing.  However, I go to bios, go to boot devices and select USB for priority one, save...and I'm left with just a blinking cursor on the top left of the screen with nothing else happening.. I  have no idea what's  going on or why it's not booting from the  usb disk. Any ideas?

---

### Post by koebln on 2012-11-29
If there is nothing but a blinking cursor while trying to boot from USB-Stick it seems to me that the computer cannot address the usb-stick. It might be an error in the installed Software, bootloader, MBR or something. Also make sure that you don't use an USB 3.0 Stick, because they might no work with only the BIOS initialisation on an older hardware. 
If you can, try that stick on an other computer to verify whether the stick or your eeepc has a problem. 

How did you create the USB-Stick? Did you use the Ubuntu "Startup Disk Creator"?

---

### Post by Ravi Bakshi on 2013-05-22
I have a chromebook c7 that was running 12.04, i upgraded to 12.10 and it bricked my whole system even dual boot chrome os. the last i saw was a message "cpu package power limit"

---

