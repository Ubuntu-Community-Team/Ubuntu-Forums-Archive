---
title: "[SOLVED] It has been so long and it still doesn't work..."
date: 2008-04-13
forum: General Help
---

### Post by Tienshinan8 on 2008-04-13
I want to run Ubuntu on my system but it has been a very long path with many hurdles to jump over and now that I have reached yet another, I will now ask for help but first I'll tell you the problems I faced so I can show my dedication to completing this task.

I have a 70 GB Hardrive that first had Windows XP on 60 GB, and a Recovery Console and other stuff on the other 10 GB.  I decided that after using the Live CD version of Ubuntu and Kubuntu that I'll install Ubuntu over the other 10 GB.  When I'm going through the installation procedure the Ubuntu installer doesn't notice my Windows XP account which is a little odd. I choose to install it anyway any its done.  When I boot up however, GRUB does not have Windows XP listed.  I go to my WinXP Recovery Console CD and "FixMBR".  When I boot up again, there is no GRUB and it goes to "Windows XP Loading" when suddenly I get a Blue Screen of Death saying "UNMOUNTABLE_BOOT_PARTITION" (I backed up my files previous to all this just in case you're wondering). Not knowing what to do, I go back to the Recovery Console and do the "FixBoot" command. When I try to boot up it complains that the NTLDR is missing.  Using my trusty KNOPPIX live CD I check the directory of my Windows partition and the file are all scrambled as in happy faces and stars and dollar signs every where.  

I then ERASE the entire hardrive using the Ultimate Boot CD and then repartition for 49 GB NTFS, 10 GB Ext3, 10 GB Ext3, and 1 GB SWAP (2 Ext3s because now I want to triple-boot WinXP, Ubuntu, and Kubuntu).  I then reinstall Windows XP (the complete procedure including, boot-up installation, graphical final installation, driver installation, anti-virus download and installation, and 70 Windows Security Updates took about 8 hours), I install Ubuntu (and this time it sees my WinXP stuff), and so far everything looks awesome.  When I install Kubuntu however, things mess up a little.  I don't know how this happened but after installing Kubuntu, Ubuntu takes twice as long to boot-up and I have to press CTRL-ALT-DEL twice during boot-up to keep it loading (there is no splash screen) and Kubuntu (again without showing me the splash screen)  loads up but I sometimes get errors like "This file is not found!" when trying to open something and when accessing the main menu instead of seeing something like "Konsole (Terminal)" I see "App name: Konsole (Terminal application)" which is like that with all the programs in the menu.  ALSO, I can configure GRUB so that WinXP is the default selection in Ubuntu but it doesn't have an effect in GRUB probably because I installed Kubuntu later, right? So when I try to edit GRUB in Kubuntu I get a access denied message.  

ALL this and I still haven't been able to connect to the INTERNET yet in either distro because it says crap like "Run sudo apt-get blahblahblah" so I can get GnomePPP in Ubuntu but if I need to connect to the internet but cannot than obviously I can't download anything! So I download the appropriate modem drivers for Ubuntu and Kubuntu and finally install them but in Kubuntu it says that I am connected but my browser says that it can't connect to anything instantly as if I'm not connected (and yes I have Work Offline deselected!) and over in Ubuntu (still without GnomePPP) it tries to connect to the internet but it starts and nothing happens! On the phone line I'm hearing this storm of noise with a recurring pattern but without quitting it never actually completes and just stays there.  

Finally I say "screw it" and I delete both Ubuntu and Kubuntu partitions with the intention of having only Ubuntu on the remaining 20 GB.  When I go through the installer I get "Cannot install Grub. This is a Fatal Error." and I can't go further so I then go and FixMBR with Recovery Console to completely clean out GRUB from the MBR and try again. I end up getting the same error.

This is the point I need help on.  GRUB won't reinstall and therefore Ubuntu won't reinstall, and I downloaded GnomePPP through WinXP but I couldn't install it. 

1. GRUB installation
2. GnomePPP installation

Linux for human beings?  I started this on before Good Friday in March. Now its April 13 and I feel like crying.

---

### Post by Trmptxn on 2008-04-13
this may sound like a stupid reply, but when i was trying to install ubuntu on my dual boot xp system, i got the same type of error, with grub not wanting to load.  it turned out the CD i burned was bad, when i ran the check CD for errors in the first menu. 

       I hope this helps, im still very new to this but there are plenty of people on these forums that im sure can help you if this doesent work.  dont worry its worth it when you get it to work =)

---

### Post by Tienshinan8 on 2008-04-13
I hope so.
By the way, my Ubuntu CD was ordered and my Kubuntu CD was burned but it was torrented.

---

### Post by Tienshinan8 on 2008-04-13
and both CDs were working well when I was using them as LiveCDs (none of that weird stuff in Kubuntu but still no Ubuntu splash screen).

---

### Post by Tienshinan8 on 2008-04-14
I just need help on getting Grub to install and to install GnomePPP!

---

