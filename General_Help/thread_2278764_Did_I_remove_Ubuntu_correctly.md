---
title: "Did I remove Ubuntu correctly?"
date: 2015-05-18
forum: General Help
---

### Post by spencer15 on 2015-05-18
[COLOR=#000000][FONT=verdana]I downloaded ubuntu few hours ago but I didn't like it. So I decided to remove ubuntu from my computer. By the way, i'm using Windows 8 and it's installed version, not cd version.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]So I opened up disk manager and deleted all the ubuntu stuffs. The tutorial said that at this point, ubuntu is deleted but its boot loader still exists.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Tutorial: [/FONT][/COLOR][http://www.howtogeek.com/141818/how-to-uninstall-a-linux-dual-boot-system-from-your-computer/](http://www.howtogeek.com/141818/how-to-uninstall-a-linux-dual-boot-system-from-your-computer/)


[COLOR=#000000][FONT=verdana]So I plugged my USB in as the tutorial says and rebooted my computer but it started grub resque? I don't know what that is but I couldn't do anything so I force turned off my computer and restarted my computer with BIOS mode. I changed boot list option to UEFI instead of Legacy (it was set it to Legacy by default). Then my computer went normal...[/FONT][/COLOR]


[COLOR=#000000][FONT=verdana]I don't feel clear about this...did I remove Ubuntu correctly? How come I didn't use the USB?[/FONT][/COLOR]

---

### Post by Bucky Ball on 2015-05-19
Welcome. Boot from the Ubuntu install media, launch the app Gparted, delete all the partitions you created during the Ubuntu install.

Don't know if you are using legacy or UEFI mode, but search for 'remove grub' for the former or 'remove uefi ubuntu entry' for the latter, all depending on which way you went. Good luck.

> **Elizine said:**
> Hi,

I will give you the solution to remove it correctly but can you specify the reason for not liking Ubuntu?

***General Help*** is a support area and user asking for support. There are chat areas to discuss the pros and cons of Ubuntu and even [a thread devoted to what you dislike about Ubuntu.]("http://ubuntuforums.org/showthread.php?t=797223&highlight=things+dislike+ubuntu") ;)

Having said that, if the OP would like to post regarding any issues they are having with Ubuntu that are putting them off the OS or would like to discuss alternatives, or even the OS, they should feel free to do so in the appropriate area here, support or otherwise. :)

---

### Post by spencer15 on 2015-05-19
Well, I removed all Ubuntu partitions from Windows 8 and I can't get into Ubuntu when I boot my computer. So how do I access Ubuntu media?

I have another question, will reinstalling my Windows 8 from the troubleshooter delete all things related to Ubuntu?

---

### Post by Bucky Ball on 2015-05-19
How to access Ubuntu media? You mean install media? Boot from whatever you installed Ubuntu with then 'Try Ubuntu' from the install media.

Have no idea what Windows troubleshooter is. A Windows question and belongs in that section here or in a Win forum (you would probably answer your own question with a little research), but what I do know is that using the Win recovery will reset your disk back to the factory default, i.e. exactly as it was when you first switched it on. That should totally wipe anything Ubuntu (as far as I know). Windowers will have a better idea of what Windows tools do what.

If you boot from the Ubuntu install media, launch Gparted, look for any partitions that are EXT* filesystem (probably EXT4), delete them, you've killed all trace of the Ubuntu partitions and OS. No idea whether you are using legacy or UEFI mode for install (please answer questions in my first post to aid future helpers), but lots of info out there about removing grub and probably about deleting Ubuntu entry from the EFI partition, too. Good luck.

PS: I came across a page at Microsoft some time ago telling how to remove Ubuntu dual-booted with a Win8 install. You might try to locate that.

---

### Post by wullus on 2015-05-19
[LIST=1]
[*]**my be you can use this step...**

[LIST]
[*]Grab a Windows recovery media or installation CD and boot from it. You should see this on a recovery media CD. ...
[*]Open the Command Prompt, then type bootrec /fixmbr into the Command Prompt.
[*]Reboot and boot into Windows. Then follow the steps below to remove the Ubuntu partitions.
[/LIST]


[/LIST]
Source: [http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)

---

### Post by RobGoss on 2015-05-19
This might come in handy trying to remove Ubuntu. [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller) When ever I removed Ubuntu I just wiped my machine and installed another distribution. Good luck

---

### Post by RobGoss on 2015-05-19
> **spencer15 said:**
> Well, I removed all Ubuntu partitions from Windows 8 and I can't get into Ubuntu when I boot my computer. So how do I access Ubuntu media?

I have another question, will reinstalling my Windows 8 from the troubleshooter delete all things related to Ubuntu?

If you removed the partition for Ubuntu you will not be able to boot in to Ubuntu boot loader or access the interface. You clearly remove something because you can't get in to the Ubuntu start-up screen. It might be to your best interest to do a fresh install for Windows 8 with your media disk if you have one.

Re-installing Windows 8 if done correctly will completely wipe the drive clean including anything that is associated with Ubuntu.

---

### Post by spencer15 on 2015-05-19
BEFORE YOU READ THIS, PLEASE TELL ME, WILL "Reset your PC" OPTION IN TROUBLESHOOTER CLEAR ALL UBUNTU STUFFS AND I DON'T HAVE TO DO ANY NASTY PARTITION KINDA STUFF? if yes, please post an answer, if no please read below...(sorry for the caps)



I think I didn't explain enough information about my installation, so here it goes. (very specifically)




My computer is Windows 8 (pre-built not cd installed) and I created a new partition for installing Ubuntu. I download Ubuntu and put it in my USB. I turned off my laptop and entered the BIOS mode. I turned off Fast boot mode, Secure boot mode to disable and boot mode to UEFI (it was UEFI by default). I put my USB and it showed me a Ubuntu screen so I installed it. Here's interesting part. Whenever I want to start up Ubuntu, I just press my power button, it will automatically start up Ubuntu (there was no stuffs like Grub or selecting operating system kinda screen). But if I want to start up Windows 8, I press power button and press f12, it will bring some kinda of blue screen (by the way is this windows boot loader?). There is "Windows boot manager", if I press this, it will start up Windows 8...So there is no stuffs like Grub or OS select screen. After I deleted Ubuntu, it starts up Windows 8 when I press power button. But I don't feel 'clean' about this, I think there are more stuffs to delete...am I wrong?

---

### Post by oldfred on 2015-05-19
Not sure if you installed Ubuntu in UEFI or BIOS boot mode.
If UEFI you have an ubuntu folder in the efi partition. Windows does not mount the efi partition normally, you have to research that if you want to use Windows.
But you can use live Ubuntu installer in live mode and delete the ubuntu folder.
You must delete ubuntu folder first as UEFI has its own NVRAM to remember boot loaders and will re-add it.
Then from efibootmgr on live installer you can remove UEFI entry. Not sure if Windows even has a way.

 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by spencer15 on 2015-05-19
I think I installed Ubuntu in UEFI mode, but if I reset my Windows 8 in troubleshooter, will all Ubuntu stuffs gone? like completely destroyed? because if it does, I will do it.

---

### Post by oldfred on 2015-05-19
The efi folder will not be replaced, and UEFI has its own NVRAM. You have to separately delete the ubuntu entries.

If you did install in BIOS/CSM mode just do not boot in that mode.
And if you have Windows set as default it really does not matter that you have other entries in UEFI.

---

### Post by spencer15 on 2015-05-19
So that means some Ubuntu files will still remain even if I reset my computer. What if I choose "Fully clean the drive" option? Will this completely remove anything related to Ubuntu?

---

### Post by oldfred on 2015-05-20
UEFI NVRAM is Non-volile RAM or memory on motherboard. So it saves entries on motherboard, not on hard drive.
You just have to remove ubuntu folder in efi partition and use efibootmgr to remove UEFI NVRAM entry. See above.

---

