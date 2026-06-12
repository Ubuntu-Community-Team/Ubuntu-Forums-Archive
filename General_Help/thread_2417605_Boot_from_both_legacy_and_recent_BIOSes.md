---
title: "Boot from both legacy and recent BIOSes?"
date: 2019-04-25
forum: General Help
---

### Post by josaphat2 on 2019-04-25
I installed Ubuntu on a USB stick (real install, not iso/live or whatsoever). I run the stick on 3 different computers.

On legacy BIOS it works well, but on newer hardware I need to set "legacy support" on the BIOS. Say this is computer A, boots to Ubuntu without a problem, this is where I build the Ubuntu stick.

Some don't have the "legacy support" but it still shows the USB stick as a boot option on the BIOS settings. If I just plug it in and turn on the computer it won't boot from the stick. However, I can enter BIOS select boot from my USB stick then the computer boot from it. This is computer B.

The problem is that another motherboard (recent ASUS laptop) don't have this "legacy support" and the stick don't show up as a boot option. Computer C.

So what can I possibly do to the install so that it can work on both legacy and newer BIOS, on all computer (A, B, C)?

Thank you in advance!

---

### Post by sudodus on 2019-04-25
The following link can help you create an installed system that boots both in UEFI mode and BIOS mode (alias CSM alias legacy mode),

[help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative-18.04.1](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative-18.04.1)

---

### Post by josaphat2 on 2019-04-25
Ah yes. UEFI. That's the term.

I think my Lenovo UEFI got this legacy mode, while my ASUS don't have any of these options to be found anywhere, so there's no possible way to boot from USB on this Asus.

"legacy" BIOS works so well within decades of computer technology and they have to change it so it become more "secure".

Locking the BIOS with password should be more than enough for offline intrusion, and who the hell needs more than 4 partitions? ](*,)

Sorry for the rant. Guess I'll have to re-do my USB with that image.

But iss there any way to convert/add UEFI support to my current USB?

[edit]

Crap I accidentally erased my ubuntu partition on the USB. using convert mbr to gpt option in Partition Wizard.

Oh well, Lubuntu is good anyway.

Thanks.

---

### Post by sudodus on 2019-04-25
If you  are happy using the system that I uploaded, fine :-)

Otherwise you can create a similar system 'from scratch' using the method that is described in the link in my first post, and you can start with standard Ubuntu or any other Ubuntu flavour.

---

### Post by josaphat2 on 2019-04-25
> **sudodus said:**
> If you  are happy using the system that I uploaded, fine :-)

Otherwise you can create a similar system 'from scratch' using the method that is described in the link in my first post, and you can start with standard Ubuntu or any other Ubuntu flavour.

I forgot I actually got clonezilla backup of my USB

I use boot-repair to convert it to EFI

Now it can boot just fine.

So as far as I can tell, grub-efi can't co-exist with the "legacy" grub? My 40_custom entries are gone, I use them to boot Android-x86 and clonezilla + gparted live cd. I placed them within folder on root. 

Anyway the method on your link uses MBR or GPT partition?

---

### Post by oldfred on 2019-04-25
There was a discussion by developers where they uninstalled one version of grub when the other version was un-installed.  So you could not have both BIOS & UEFI grub installed at same time. Workaround was to install one and configure it, then install the other.
But discussion said they were going to change to allow both applications to be installed, but that not not necessarily mean you have both configured.

When every you fully reinstall any version of grub the configuration files are rewritten. Any file you edit in /etc should be backed up. i only edit a few, so copy into /home, so my regular backup of /home includes those files. Otherwise fully backup all of /etc.

---

### Post by sudodus on 2019-04-26
> **josaphat2 said:**
> I forgot I actually got clonezilla backup of my USB

I use boot-repair to convert it to EFI

Now it can boot just fine.

So as far as I can tell, grub-efi can't co-exist with the "legacy" grub? My 40_custom entries are gone, I use them to boot Android-x86 and clonezilla + gparted live cd. I placed them within folder on root. 

Anyway the method on your link uses MBR or GPT partition?

In a live or persistent live system grub-efi can co-exist with the "legacy" grub, but not in an installed system.

In an installed system you can use one of the grub versions to configure for example legacy boot, remove it and install the other version to configure UEFI boot.

The method in my link (via mkusb) can work both with MBR (alias MSDOS partition table) and GPT. The default is GPT (but some HP computers are unwilling to boot from grub in legacy mode with GPT, so MBR is provided).

---

### Post by josaphat2 on 2019-04-26
> **oldfred said:**
> There was a discussion by developers where they uninstalled one version of grub when the other version was un-installed. So you could not have both BIOS & UEFI grub installed at same time. Workaround was to install one and configure it, then install the other.
But discussion said they were going to change to allow both applications to be installed, but that not not necessarily mean you have both configured.

When every you fully reinstall any version of grub the configuration files are rewritten. Any file you edit in /etc should be backed up. i only edit a few, so copy into /home, so my regular backup of /home includes those files. Otherwise fully backup all of /etc.

It is understandable since GPT isn't backward compatible with MBR as far as I perceive. Some readings to do about MBR vs GPT.

I'm clueless about grub-efi configuration though. I'll take a look at them later. I still have 40_custom file inside my backup. And I haven't examine my grub.cfg file yet. I'll do them ASAP after I get my hands on the USB again.

In the meanwhile, I won't mind some pointers :


[LIST=1]
[*]Would the configuration be similar to legacy grub? But this time the menu entry refers to the GPT partition instead of 'MSDOS'
[*]Also how to boot clonezilla EFI (alternative-stable) from ISO? And Android-x86 (real install) from EFI? I've been looking around their websites, seems that there's no manual on how to set them up on UEFI :confused:
[/LIST]

> **sudodus said:**
> In a live or persistent live system grub-efi can co-exist with the "legacy" grub, but not in an installed system.

In an installed system you can use one of the grub versions to configure for example legacy boot, remove it and install the other version to configure UEFI boot.

The method in my link (via mkusb) can work both with MBR (alias MSDOS partition table) and GPT. The default is GPT (but some HP computers are unwilling to boot from grub in legacy mode with GPT, so MBR is provided).

So basically installed version NEED to be on MBR?

UEFI can only co-exist with installed version if it's set in live mode?

Eh, for the USB I'm ready to ditch legacy grub/MBR anyway, since most computers now should use UEFI.

The only thing that still uses pure legacy BIOS I own is 12 years old netbook.

Thank you in advance!

---

### Post by oldfred on 2019-04-26
I started using gpt in 2010 with BIOS only system and it needs a bios_grub partition. And every new drive or totally repartitioned drive was converted to gpt.
When Windows required UEFI/gpt with release of Windows 8, I knew eventually I would have a UEFI system and started adding both an ESP - efi system partition  the bios_grub to every new drive. When flash drives got larger, I often put a full UEFI install with gpt partitioning on it.

       [URL="http://www.rodsbooks.com/gdisk/whatsgpt.html"]http://www.rodsbooks.com/gdisk/whatsgpt.html
      [/URL]
 [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

You never want this, which sometimes was used with Mac in UEFI and when Windows was only BIOS and had to have MBR.
       
 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

The gpt has a protective MBR, just so old partition tools (like fdisk until recently) would not see drive as unpartitioned. You will have on MBR entry saying drive is gpt. Then  you have gpt partition table with your actual partitions.
 

    
 

    [URL="http://www.rodsbooks.com/gdisk/whatsgpt.html"]
[/URL]

---

### Post by sudodus on 2019-04-26
> **josaphat2 said:**
> So basically installed version NEED to be on MBR?
No> 
UEFI can only co-exist with installed version if it's set in live mode?
I don't understand what you mean.> 
Eh, for the USB I'm ready to ditch legacy grub/MBR anyway, since most computers now should use UEFI.

The only thing that still uses pure legacy BIOS I own is 12 years old netbook.

Thank you in advance!
If you are ready to ditch legacy boot, you should boot your live system in UEFI mode and install Ubuntu. Then it will be installed in UEFI mode.

Edit: See [How do I install Ubuntu to a USB key? (without using Startup Disk Creator)](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312)

---

### Post by josaphat2 on 2019-04-27
> **oldfred said:**
> I started using gpt in 2010 with BIOS only system and it needs a bios_grub partition. And every new drive or totally repartitioned drive was converted to gpt.
When Windows required UEFI/gpt with release of Windows 8, I knew eventually I would have a UEFI system and started adding both an ESP - efi system partition  the bios_grub to every new drive. When flash drives got larger, I often put a full UEFI install with gpt partitioning on it.

       [URL="http://www.rodsbooks.com/gdisk/whatsgpt.html"]http://www.rodsbooks.com/gdisk/whatsgpt.html
      [/URL]
 [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

You never want this, which sometimes was used with Mac in UEFI and when Windows was only BIOS and had to have MBR.
       
 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

The gpt has a protective MBR, just so old partition tools (like fdisk until recently) would not see drive as unpartitioned. You will have on MBR entry saying drive is gpt. Then  you have gpt partition table with your actual partitions.
 
Even after reading some stuffs about GPT and UEFI I still don't get it.

ROFLMAO

But hey, technology.

[IMG]https://media.giphy.com/media/3kgASaXXX3wY/source.gif[/IMG]

oh yeah, also grub-efi configuration is pretty much the same. Just need to change "sda, sdb" or "hdx,x" thingy to "hdx, gptx"

> **sudodus said:**
> NoI don't understand what you mean.
If you are ready to ditch legacy boot, you should boot your live system in UEFI mode and install Ubuntu. Then it will be installed in UEFI mode.

Edit: See [How do I install Ubuntu to a USB key? (without using Startup Disk Creator)]("https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312")

I already sorted it out.

The USB now boots from UEFI, everything still left intact.

Thanks for the help!

Although I'm still curious about the Lubuntu image. I'll give it a go when I got the time and machine to do it.

---

