---
title: "Triple Boot UEFI Problems [requires a second boot on grub]"
date: 2018-02-12
forum: General Help
---

### Post by rhaes on 2018-02-12
Hello,

I am having difficulties getting my grub menu to work in a triple boot. I have Windows 7 and 10 on seperate drives, and a Ubuntu 16.04 on another drive. I installed as UEFI on all of them in this process: turn on BIOS option for UEFI > create bootable UEFI USBs for both Windows using Rufus and setting it to GPT and FAT32 > wipe drives > install Windows 7 > install Windows 10 > install Ubuntu > boot-repair > boot off drive that says Ubuntu.

Now I got the grub menu as normal, purple and all, but what I got was strange. Instead of the os-prober getting the entries as Ubuntu and Windows, I got this mess instead:

[https://imgur.com/F1jT704](https://imgur.com/F1jT704)
*image appears super big on forum for some reason

Now I thought nothing of it because I could also use grub customizer to rename them, however, they do not function anything like the BIOS/Legacy grub menu entries did. Instead of clicking say Windows 7, it takes me to Windows 10 dual boot screen (blue, looks like this) and that's not so bad, but if I click any of them, it reboots me back to the grub menu and I have to boot into Windows again for it to actually boot into whatever I selected when I got the Win10 boot screen. Ubuntu boots fine on first try though. Before, on Legacy mode, my grub menu even on triple boot would allow me to select either Win7 or Win10 and it would immediately launch into them, now the boot times are very long because of it needing a second boot on top of another boot menu created by Windows 10. 

Now I have googled this like mad in various ways, but I'm guessing my wording is sloppy or something. So I came here in desperation (been at it for two days).  Is there something I am missing? Would someone be kind enough to help me out here? First time I have installed a system with UEFI so I probably screwed something up...

Thank you!

---

### Post by oldfred on 2018-02-12
I do not think you are missing anything.

With UEFI systems boot from the ESP - efi system partition.
And all Windows UEFI systems only have one folder /EFI/Microsoft. So then last install will be in control and then in BCD you choose which Windows to boot.
Note that Windows 7 does not support UEFI Secure boot at all. And if Windows 10 fast start up/hibernation is on, it may prevent or interfere with booting the other Windows as well as Ubuntu.

Somewhat same with Ubuntu. You only have one /EFI/ubuntu folder. And then last install is version in that folder and controls booting. 
Then from grub menu you can boot all your other installs.

Some have created a second ESP. Not sure how that works as most system only allow one ESP per drive. Users must then move boot flag changing which FAT32 partition is then the active ESP?

---

### Post by rhaes on 2018-02-13
Hello and thank you for the reply,

It is good to know I followed the guide I found correctly. There were so many different ways that I had to just pick one. 

Oh, and I have disabled fast boot, MSI fast boot and did what I thought solved hibernation on Windows 10. I went into CMD as admin and disabled it with powercfg.exe /hibernation off. I even did the same in Windows 7, but unfortunately it hasn't solved anything. I do not know how to check if secure boot is on or off, but I went through my BIOS and I disabled all Windows specific features and couldn't locate anything like that. I will look again in a moment, see if I missed anything.

>  Some have created a second ESP. Not sure how that works as most system  only allow one ESP per drive. Users must then move boot flag changing  which FAT32 partition is then the active ESP? 				

I'm sorry, but I do not know what ESP is. :oops:

---

### Post by oldfred on 2018-02-13
With UEFI systems boot from the ESP - efi system partition.
Which is then the FAT32 partition with the boot flag.
[https://en.wikipedia.org/wiki/EFI_system_partition](https://en.wikipedia.org/wiki/EFI_system_partition)

Many UEFI systems have setting "Windows" or "Other". Fine print says to use "Other" for Windows 7.
So that is really the secure boot setting as Windows 7 does not support UEFI Secure Boot.

Note that Windows 10 updates may turn fast start up back on.
So if issues with booting Windows 7 or Ubuntu seeing NTFS partitions, check that setting again.

---

### Post by rhaes on 2018-02-13
Hello,

Well I ended up checking to see if Secure Boot was in my BIOS. It is not. However, I double checked all other Windows specific features or boot features and made sure they were disabled. Unfortunately, it did not solve anything.

However, I have found a **solution**. Granted this would be easier on a fresh install, I didn't want to deal with Windows 7 support telling me my key was an upgrade key only, so this is what I did.

I turned off my PC and unhooked the Ubuntu and Windows 10 drive and any storage drives or USBs. Next, I booted into Windows 7 recovery using my DVD. I selected "Repair this computer" and then selected my Win7 OS from the list of Windows 10 or Windows 7. Next, I opened the command prompt option and started a boot repair on it using these commands so that I could boot into the OS again:

```
 
Step 1: bootrec /fixboot
Step 2: bootrec /fixmbr

```

Rebooting allowed me to access Windows 7 from BOOT menu on my BIOS (by pressing F11 and selecting the Win7 drive manually). Now I needed to get rid of the black grub menu that was preventing me still from booting normally into Windows 7, but first I needed to also get rid of the Win10 garbage left behind, so the next thing I did was log into Windows 7 and open MSCONFIG with Windows Key + R. In here, I went to BOOT and selected the leftover Windows 10 and deleted it, applied and then exited out without a reboot. 

Next, it was grub removal time. I had to navigate to the EFI ubuntu folder on the Win7 drive and delete it. I did this by opening CMD as admin. I'd detail this part, but I'd butcher it, so instead I'll link to the post that I followed:

> 
You will be doing this from Windows 10. No bootable media required. 


  Where bootrec /fixmbr, bootsect /nt60 and the Ubuntu live with the boot-repair suggestions have failed, this has worked for me:


  (This answer borrowed verbatim from [here]("http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/"))


  
[LIST=1]
[*]Run a cmd.exe process with administrator privileges 
[*]Run diskpart 
[*]Type: list disk then sel disk X where X is the drive your boot files reside on 
[*]Type list vol to see all partitions (volumes) on the disk 
[*]Select the EFI volume by typing: sel vol Y where Y is the SYSTEM volume (this is almost always the EFI partition) 
[*]For convenience, assign a drive letter by typing: assign letter=Z: where Z is a free (unused) drive letter 
[*]Type exit to leave disk part 
[*]While still in the cmd prompt, type: Z: and hit enter, where Z was the drive letter you just created. 
[*]Type dir to list directories on this mounted EFI partition 
[*]If you are in the right place, you should see a directory called EFI 
[*]Type cd EFI and then dir to list the child directories inside EFI 
[*]Type rmdir /S ubuntu to delete the ubuntu boot directory 
[/LIST]
  
Assuming you only ever had two operating systems (Win 10 &  Ubuntu) you should now be able to boot directly to Windows without  hitting the black grub screen.



**Source:** [https://askubuntu.com/questions/429610/uninstall-grub-and-windows-bootloader](https://askubuntu.com/questions/429610/uninstall-grub-and-windows-bootloader)

I'm sure you can probably do the same thing from a DVD for Windows (and I did this in Windows 7, not 10, so it works either way), but thankfully I could get into my drive to do it from the OS. 

Now, to get the original functioning grub so I didn't have to boot twice into whatever Windows OS I selected. The problem was installing Windows 10 last beforehand, triggering it I guess to make its own boot menu on top of grub. I achieved the fix by doing this:

1. unplug all drives EXCEPT the one drive with Windows 10 on it that I would be reinstalling over / the drive I intended to use for Windows 10

2. boot up UEFI USB I made with Rufus

3. Reinstall Windows 10

With Windows 10 done and my Windows 7 install fixed and no longer attached to Windows 10 or grub, I powered off again. I unplugged Windows 10's drive and then plugged in the drive I wanted for Ubuntu back in, making sure it was the only drive hooked up. Booting up *boot-repair* could not save her though, so I had to reinstall. Unfortunately, I ran into a slight hiccup as my installer crashed once. So I rebooted back into the Live USB and clicked the* Try Ubuntu Before Installing* again.

This time I opened up* gparted* and deleted the Ubuntu partitions so it was one unallocated space. Two minor partitions refused to delete though, so I had to right click them and click SWAPOFF. It then allowed me to delete all partitions. I applied the actions by clicking the green check mark and then began the installation process again. 

Once it was finished installing Ubuntu, I shut down the computer and plugged in the Windows 7 and Windows 10 drive and booted back up. I was instantly logged into Ubuntu, which is what I wanted. If one is not booted into it, you can manually boot into Ubuntu by getting into your BIOS boot menu. 

Inside of the fresh install, I installed *boot-repair* and *grub customizer*.

```

sudo add-apt-repository ppa:yannubuntu/boot-repair

sudo apt-get update

sudo apt-get install -y boot-repair

```

And

```


sudo add-apt-repository ppa:danielrichter2007/grub-customizer

sudo apt-get update

sudo apt-get install grub-customizer

```

Next I opened up boot-repair and did the **recommended step option**. It had me do some terminal manual steps, like deciding where to place my grub, and then I was done. Without rebooting, I closed down the boot-repair pop ups and then opened grub customizer.

In here, I had a whole slew of options, most with the crazy looking bootxx.efi and other efi files. I clicked one of them, right clicked and created a new sub-folder and moved all of those crazy options into it. Next, I located the boot entries that would take me into Windows. For example, mine were;

Windows Boot Loader (/dev/sdX)
Windows Boot Loader (/dev/sdX)
*where x is each separate drive/install

I knew where I installed Windows 7 too, so I knew the first dev/sdx was my Win7 and so the other was Win10. So I double clicked them and renamed them to simple things like "Windows 7" and "Windows 10". If anyone reading this cannot figure it out or remember where they installed, you can reboot here and boot into each entry, remember which you booted into, and then recording it down so that when you boot back into Ubuntu for this step, you can appropriately rename them! :)

I then pressed the **Save button** and opened a new terminal and updated the grub:

```


sudo update-grub


```

And then I rebooted, and I had a simple purple grub menu again and I didn't have to deal with the double booting for Windows (I blame Windows 10 entirely for that headache!) and they were all still UEFI! :)

*Obviously if you are starting fresh rather than trying to save an OS like I needed to for Windows 7, you just install each OS separately as UEFI. This means unplugging all other drives and then when you move to the next OS, unplug the previous OS drive and so on. *

Well, I hope this helps others who triple boot like me and came across this, or anyone at all.;)



_**P.S**_

Sadly I have found that in UEFI mode, one cannot use ext2explore on Windows to explore the Ubuntu drive any further! OUCH! :-({|=

---

### Post by 1clue on 2018-02-13
GPT partition tables don't have a boot flag. If you have an option to set a boot flag then either you don't have a GPT partition table or you have a combination MBR/GPT partition table, which IMO leads to confusion and possible damage/destruction when using the wrong type of partition editor.

The boot partition needs to be partition type ef00 and be fat32 formatted.

Sorry I only read down to where people started talking about "boot flag" and posted.

For me, the ef00 partition is 500M mostly because I compile a lot of kernels and like to keep a few spares. Regardless some documentation (not necessarily Ubuntu) gives ridiculously small ef00 partition sizes and this messes a lot of people up. The ef00 partition needs to have enough room for the kernel(s) and/or boot loader, and all associated files.

Another thing: My entire /boot is the ef00 partition. There is nothing in /boot which can't be on the efi boot partition. UEFI does not know where the partition is mounted when the system is up, and it does not care what else is on the filesystem. There is nothing in /boot which can't be on fat32.

The efiboot directories are paths from the root of the ef00 partition. That's all you need to keep in mind.

---

### Post by oldfred on 2018-02-13
Gparted does use boot flag to indicate the ESP - efi system partition.
But with gpt it has a totally different meaning than with BIOS/MBR configuration.

Both gparted's boot flag and gdisk's ef00 are really assigning a very long Partition type GUID to the ESP partition. And it is the GUID that UEFI is looking for.
       [URL="http://en.wikipedia.org/wiki/GUID_Partition_Table"]http://en.wikipedia.org/wiki/GUID_Partition_Table
      [/URL]
 EFI System partition - 	C12A7328-F81F-11D2-BA4B-00A0C93EC93B 

    [URL="http://en.wikipedia.org/wiki/GUID_Partition_Table"]
[/URL]

---

### Post by rbmorse on 2018-02-15
Look at rEFInd.  It was created specifically to act as a boot selector/manager on machines with multiple UEFI operating systems installed. I use it to quad-boot Windows 10, Ubuntu 17.1, Linux Mint and Fedora.  If a USB drive with an EFI operating system is plugged unto a port when the machine is booted, rEFInd will detect and enumerate it, too (i.e., clonezilla or systemrescue.cd).  

rEFInd can be installed is a variety of ways, but the easiest, assuming one can boot into a Ubuntu session, is to add the .ppa  to the repository list and install rEFInd as a normal package. The installer will find all of the valid .efi boot signatures on the machine and automagically add them to the boot menu. 

Details at:

[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

