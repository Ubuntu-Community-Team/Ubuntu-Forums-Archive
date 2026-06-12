---
title: "Set GRUB as the default bootloader over Windows Boot Manager?"
date: 2014-08-28
forum: General Help
---

### Post by SLaCK3r on 2014-08-28
Hi, everyone. I've been using Ubuntu for a while now. Consistently for the past 2 weeks, but I've experimented with it over the years.

I really love it. I've solved almost all of my hardware issues on my HP Envy 15TS (2013) PC. I am currently dual-booting with Windows 8.1 (only because in my Cycber Security classes, labs are written for Windows PCs). I have disabled UEFI boot and have tried to set the boot managers around so that it won't autoboot to Windows 8.1, but I can't get it to work.

I have tried the bcdedit in Windows, disabled fastboot, but to no avail. I am using an HP BIOS so I have only a few options in BIOS. To boot to Ubuntu, I must pres my F9 key to access the boot options every time I start up and select "Ubuntu [my harddrive manufacturers name here]". It is one step below OS Boot Manager (only boots to Windows).

How can I set the default boot manager to GRUB? It seems like the better choice to quickly boot to Ubuntu and also it givs me the option to boot to Windows if I need to. Any help is appreciated, thanks!

Boot Repair gives me this with an error of the boot being too far from the start of the disk: [http://paste.ubuntu.com/8168998/](http://paste.ubuntu.com/8168998/)

---

### Post by Krupski on 2014-08-28
> **SLaCK3r said:**
> Hi, everyone. I've been using Ubuntu for a while now. Consistently for the past 2 weeks, but I've experimented with it over the years.

I really love it. I've solved almost all of my hardware issues on my HP Envy 15TS (2013) PC. I am currently dual-booting with Windows 8.1 (only because in my Cycber Security classes, labs are written for Windows PCs). I have disabled UEFI boot and have tried to set the boot managers around so that it won't autoboot to Windows 8.1, but I can't get it to work.

I have tried the bcdedit in Windows, disabled fastboot, but to no avail. I am using an HP BIOS so I have only a few options in BIOS. To boot to Ubuntu, I must pres my F9 key to access the boot options every time I start up and select "Ubuntu [my harddrive manufacturers name here]". It is one step below OS Boot Manager (only boots to Windows).

How can I set the default boot manager to GRUB? It seems like the better choice to quickly boot to Ubuntu and also it givs me the option to boot to Windows if I need to. Any help is appreciated, thanks!

Boot Repair gives me this with an error of the boot being too far from the start of the disk: [http://paste.ubuntu.com/8168998/](http://paste.ubuntu.com/8168998/)

You can install GRUB to your Windows drive and let it give you the menu to choose Linux or Windows.

You need to be sure first that the "grub-install" utility can see your OS installs (including Windows) so that it adds an entry for it.

**_Assuming_** that your Windows install resides on drive /dev/sda1 and /dev/sda2, you would use the following command:

[COLOR=#FF0000]**(Note this is an EXAMPLE. _DO NOT type or enter this command_ until you are 100% sure of what you are doing!)**[/COLOR]

[FONT=monospace][COLOR=#000000][SIZE=3]grub-install /dev/sda[/SIZE][/COLOR][/FONT]

To be sure GRUB scans for all of your OS installs, check in this directory:

[FONT=monospace][COLOR=#000000][SIZE=3]/etc/grub.d[/SIZE][/COLOR][/FONT]

...and be sure that all of the files in there are set as executable (that is, [FONT=monospace][COLOR=#000000]chmod 0755 * inside the directory[/COLOR][/FONT]).

At the very least, the following files should be set as executable:
[FONT=monospace][COLOR=#000000][SIZE=3]
00_header
05_debian_theme
10_linux
30_os-prober
30_uefi-firmware <-- if you use EFI[/SIZE][/COLOR][/FONT]

The ones that are executable are the ones that grub-install will use. For example, LEAVING OUT "30_os-prober" (that is, making it non-executable) will cause grub-install to not search for, find or include any other OS installs you may have in it's menu.

If you run as a user (i.e. non-root) then be sure to preface your commands with "sudo", then enter the root password when asked.

Personally, I do it the other way (I used BCDEDIT to make a Linux entry in the Windows boot menu), but either way will work.

Hope this helps.

---

### Post by Mark Phelps on 2014-08-28
Windows will NOT boot from GRUB, regardless of how you set it up.  GRUB simply passes control to the Windows boot loader in the partition you point it to.

---

### Post by SLaCK3r on 2014-08-28
> **"Krupski"]You can install GRUB to your Windows drive and let it give you the menu to choose Linux or Windows.

You need to be sure first that the "grub-install" utility can see your OS installs (including Windows) so that it adds an entry for it.

Assuming that your Windows install resides on drive /dev/sda1 and /dev/sda2, you would use the following command:

(Note this is an EXAMPLE. DO NOT type or enter this command until you are 100% sure of what you are doing!)

grub-install /dev/sda

To be sure GRUB scans for all of your OS installs, check in this directory:

/etc/grub.d

...and be sure that all of the files in there are set as executable (that is, chmod 0755 * inside the directory).

At the very least, the following files should be set as executable:

00_header
05_debian_theme
10_linux
30_os-prober
30_uefi-firmware <-- if you use EFI

The ones that are executable are the ones that grub-install will use. For example, LEAVING OUT "30_os-prober" (that is, making it non-executable) will cause grub-install to not search for, find or include any other OS installs you may have in it's menu.

If you run as a user (i.e. non-root) then be sure to preface your commands with "sudo", then enter the root password when asked.

Personally, I do it the other way (I used BCDEDIT to make a Linux entry in the Windows boot menu), but either way will work.

Hope this helps. [/quote]

Hey thanks for the assitance! I tried it using BCDEDIT and also EasyBCD in Windows to no luck. I got it to boot to the Windows black and white command bootloader, but with no Ubuntu option. 

[QUOTE=Mark Phelps said:**
> Windows will NOT boot from GRUB, regardless of how you set it up.  GRUB simply passes control to the Windows boot loader in the partition you point it to.

Yes, sorry. That's exactly what I want to do. But I can't even get that to work. These are my partititions: [img]http://imgur.com/GoGcY2a.png[/img]

---

### Post by Krupski on 2014-08-28
> **Mark Phelps said:**
> Windows will NOT boot from GRUB, regardless of how you set it up.  GRUB simply passes control to the Windows boot loader in the partition you point it to.

Yes I know that GRUB does not actually load the Windows boot code, but GRUB can ultimately "start up" Windows (or any other OS for that matter). Is that process not called "booting"?

If you really want to be ridiculous, you can say that the Windows boot loader does not boot the computer, the BIOS code does... [IMG]http://www.hobbytent.com/images/smilies/rolleyes.gif[/IMG]

---

