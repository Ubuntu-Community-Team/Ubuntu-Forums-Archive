---
title: "EFI booting hangs"
date: 2024-02-12
forum: General Help
---

### Post by Melab on 2024-02-12
I have a fit-PC3 on which I am trying to boot Linux in EFI mode. The problem is that the booting process (or maybe it's just the graphics) hangs right when GRUB2 says that it is loading the initrd. It doesn't matter if it's an already-setup Ubuntu installation, the Ubuntu installer ISO, or another distro's installer or installation. No further updates to the display happen.

To find out if it is just a case of graphics not working and that the OS is actually booting up and running, I wrote a script that I included in my initramfs on my bootable Ubuntu USB which mounts a partition and appends information about the motherboard on which the OS is running to a log on the mounted partition. I verified that it works on other computers, but nothing is recorded when booting my USB's kernel on my fit-PC3.

Things I have tried which don't work:

[LIST]
[*]Using a different bootloader. The same problem happens when I used rEFInd.
[*]Using the boot option "nomodeset".
[*]Using the boot options "acpi=off" and "pci=biosirq" as in [this solution]("https://bbs.archlinux.org/viewtopic.php?pid=1889420#p1889420") to a similar-sounding problem.
[*]Talking to the manufacturer. They wouldn't even try to reproduce the problem.
[/LIST]

How might I fix this?

Note, that I can boot Linux successfully in BIOS mode. Also, I know that my USB drive boots just fine in EFI mode on other computers, so the fit-PC3's EFI is likely buggy/flawed is thus the likely culprit. But, that doesn't mean some combination of boot options/paramters, modules, and whatever else can't solve this.

Finally, please don't ask me why I want to use EFI mode instead of BIOS mode. I just do and discussing my reasons will only bog down the thread.

---

### Post by oldfred on 2024-02-12
How much RAM?
I could not install Ubuntu 20.04 (only as test) on my 2006 BIOS only laptop. Laptop only has 1.5 GB of RAM and old slow HDD.
Both batteries are dead, but as long as connected to power it works.
I was able to install server & add lightweight gui.
I then tried Kubuntu which I normally use on newer desktop & laptop. And was surprised it was light enough to work.

Or long way of saying have you tried a lighter weight flavor.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

### Post by dragonfly41 on 2024-02-12
When recently booting into my Windows 10 dual boot I discovered a Windows only app named EasyUEFI.This is available (as are many Windows apps) on a free 15 days trial basis after which purchase is needed. But during the trial period you can inspect your EFI settings. I complicate matters by adding rEFInd.

---

### Post by Melab on 2024-02-12
> **oldfred said:**
> How much RAM?
I could not install Ubuntu 20.04 (only as test) on my 2006 BIOS only laptop. Laptop only has 1.5 GB of RAM and old slow HDD.
Both batteries are dead, but as long as connected to power it works.
I was able to install server & add lightweight gui.
I then tried Kubuntu which I normally use on newer desktop & laptop. And was surprised it was light enough to work.

Or long way of saying have you tried a lighter weight flavor.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

If RAM is not a problem in BIOS mode, then I'm pretty sure it's not the problem in EFI mode.

I've tried lighter distros and it is still the same problem.

---

### Post by Melab on 2024-02-12
> **dragonfly41 said:**
> When recently booting into my Windows 10 dual boot I discovered a Windows only app named EasyUEFI.This is available (as are many Windows apps) on a free 15 days trial basis after which purchase is needed. But during the trial period you can inspect your EFI settings. I complicate matters by adding rEFInd.

[LIST=1]
[*]I don't have a Windows installation for my fit-PC3.
[*]I wouldn't even know what settings to look for.
[*]Even if I did know what settings to look for, going by the screenshots, it looks like it only controls boot entries.
[/LIST]

---

### Post by dragonfly41 on 2024-02-12
I should have researched more.


fit-PC3
fit-PC Slim has General Software BIOS supporting PXE and booting from a USB CDROM or USB thumb drive. It is pre-installed with either Windows Vista or with Ubuntu 8.10 and Gentoo Linux 2008.0 . Also Windows Embedded can be used, or pre-installed on a FlowDrive.

But above refers to Windws Vista.  So be it.

---

### Post by Melab on 2024-02-12
> **dragonfly41 said:**
> I should have researched more.


fit-PC3
fit-PC Slim has General Software BIOS supporting PXE and booting from a USB CDROM or USB thumb drive. It is pre-installed with either Windows Vista or with Ubuntu 8.10 and Gentoo Linux 2008.0 . Also Windows Embedded can be used, or pre-installed on a FlowDrive.

But above refers to Windws Vista.  So be it.

I don't have a fit-PC Slim. That's not my device.

---

### Post by tea for one on 2024-02-13
I notice that this has been on your radar since August 2020?
[https://askubuntu.com/questions/1268320/linux-wont-start-on-fit-pc3](https://askubuntu.com/questions/1268320/linux-wont-start-on-fit-pc3)

Some suggestions:-

Have you tried using rEFInd on a portable USB device?
You have the option of launching an EFI shell.
Does the shell appear?

Remove the internal disk(s)
Can you boot anything in UEFI mode?

Is your UEFI firmware the latest iteration?

> Finally, please don't ask me why I want to use EFI mode instead of BIOS mode. I just do and discussing my reasons will only bog down the thread. 
I have to ask - it's giving me sleepless nights...........8-[

---

### Post by MAFoElffen on 2024-02-14
Fit-PC's Support has two different instructions for booting UEFI USB install disks on their machines, based on if their PC has either AMI or Phoenix BIOS...

Basically for both, they recommend that the USB installer be created using Rufus, with a GPT partition table... Here's where the differences are:

For Phoenix BIOS:
> 
 
[LIST]
[*]On the target PC set USB to be the first boot device in the boot order (BIOS defaults). 
[*]Connect the prepared bootable USB drive to the target PC and boot from it. 
[*]Press F5 during boot until the One-Time-Boot menu appears. 
[*]Browse to the Main -> Boot Features menu and set the CSM Support setting to No. 
[*]Press F10 and Yes to save the changes, and Exit. 
[*]Press F5 during boot until the One Time Boot menu appears. 
[*]Choose the USB HDD option from the list of bootable devices. 
[*]The system will boot from the installation media. 
[/LIST]
 
For AMI BIOS:
> 

[LIST]
[*]Connect the created media to the PC. 
[*]Power up the PC. 
[*]Press the F7 key during the BIOS boot until the One Time boot menu appears. 
[*]Choose the installation media device. 
[*]The system will boot from the installation media. 
[/LIST]


---

### Post by Melab on 2024-02-17
> **tea for one said:**
> 
Have you tried using rEFInd on a portable USB device?


Yes, as I said in my OP.

> **tea for one said:**
> 
You have the option of launching an EFI shell.
Does the shell appear?


Yes.

> **tea for one said:**
> 
Remove the internal disk(s)
Can you boot anything in UEFI mode?


I have attempted this both with and without the internal drive. I have been able to boot GRUB, rEFInd, and systemd-boot.

> **tea for one said:**
> Is your UEFI firmware the latest iteration?

It is the second latest.

> **tea for one said:**
> I have to ask - it's giving me sleepless nights...........8-[

I like EFI.

---

### Post by Melab on 2024-02-17
> **MAFoElffen said:**
> Fit-PC's Support has two different instructions for booting UEFI USB install disks on their machines, based on if their PC has either AMI or Phoenix BIOS...

Basically for both, they recommend that the USB installer be created using Rufus, with a GPT partition table... Here's where the differences are:

Wait, what? I already have an installation. The problem is that it won't boot Linux (or it doesn't seem to boot it) in EFI mode.

---

### Post by tea for one on 2024-02-18
> **Melab said:**
> I like EFI.
Me too

As you can use a portable rEFInd to access an EFI shell, have you tried to boot the kernel directly (i.e. avoiding grub)?
There should be an icon for this choice.
For an installed system, something like  - "boot\vmlinuz-6.2.0-35-generic from 30 GiB ext4 volume"

Your UEFI firmware being the second latest, is the latest still available?

---

### Post by Melab on 2024-02-18
> **tea for one said:**
> 
As you can use a portable rEFInd to access an EFI shell, have you tried to boot the kernel directly (i.e. avoiding grub)?


No, because the shell does not have the facilities for booting Linux with an initramfs and boot options.

> **tea for one said:**
> 
There should be an icon for this choice.
For an installed system, something like  - "boot\vmlinuz-6.2.0-35-generic from 30 GiB ext4 volume"


I don't know if you are talking about rEFInd or the EFI shell now. If you are talking about rEFInd, then doesn't that require configuration instead of it dynamically building a list of bootable Linux targets? If you are talking about rEFInd, then as I already mentioned, I've already tried using it to boot Linux with a pre-configured pairing of kernel, initramfs, and boot options.

> **tea for one said:**
> Your UEFI firmware being the second latest, is the latest still available?

Yes, but I do not want to update it until I find out how I can create a backup of the UEFI/BIOS SPI flash contents from within Linux (I do not have a flash connector and I do not want to take apart my fit-PC3).

---

### Post by oldfred on 2024-02-18
Most systems update from within UEFI as UEFI is designed to read FAT32 partitions.
Often 3 ways, from Windows, from a USB flash drive or from a FAT32 partition on your internal drive.
Many newer mainstream systems also now can be updated from Linux with fwupdate.

It looks like for Linux, you can use a flash drive.
[https://fit-pc.com/wiki/index.php?title=Airtop3_I3M_firmware_update&mobileaction=toggle_view_desktop](https://fit-pc.com/wiki/index.php?title=Airtop3_I3M_firmware_update&mobileaction=toggle_view_desktop)

---

### Post by tea for one on 2024-02-19
> **Melab said:**
> I don't know if you are talking about rEFInd or the EFI shell now. 
I was referring to using rEFInd on a portable USB device.
Assuming that your installed Ubuntu OS is built correctly with an ESP, rEFInd has an option to boot the kernel without any "pre-configuration"
The screenshot attached displays the option.

---

### Post by tea for one on 2024-02-19
> **Melab said:**
> I have a fit-PC3 on which I am trying to boot Linux in EFI mode. The problem is that the booting process (or maybe it's just the graphics) hangs right when GRUB2 says that it is loading the initrd. It doesn't matter if it's an already-setup Ubuntu installation,
The text above is from post no.1.
As you cannot boot in EFI mode, did you make this "already-setup installation" on a different PC?
Swapping Ubuntu disks between PCs is often successful if there is no esoteric hardware involved.

---

### Post by oldfred on 2024-02-19
You have some other issue.

I have used a grub BIOS boot stanza on old HDD to boot my UEFI install on external SSD.

So once grub had started loading boot stanza you have booted grub in UEFI mode. 
Then it really does not matter if UEFI or BIOS as you load kernel & drivers to finish boot.

---

### Post by Melab on 2024-02-19
> **oldfred said:**
> Most systems update from within UEFI as UEFI is designed to read FAT32 partitions.
Often 3 ways, from Windows, from a USB flash drive or from a FAT32 partition on your internal drive.
Many newer mainstream systems also now can be updated from Linux with fwupdate.

It looks like for Linux, you can use a flash drive.
[https://fit-pc.com/wiki/index.php?title=Airtop3_I3M_firmware_update&mobileaction=toggle_view_desktop](https://fit-pc.com/wiki/index.php?title=Airtop3_I3M_firmware_update&mobileaction=toggle_view_desktop)

I don't want to attempt an update of the firmware until I have created a backup of the current flash chip contents and until I feel confident enough to update it without problems.

Also, that is NOT my PC.

---

### Post by Melab on 2024-02-19
> **tea for one said:**
> I was referring to using rEFInd on a portable USB device.
Assuming that your installed Ubuntu OS is built correctly with an ESP, rEFInd has an option to boot the kernel without any "pre-configuration"
The screenshot attached displays the option.

How does it know what the target root device is? Or which initramfs to use?

My installation is already on a portable USB, not an internal SSD/HDD, and I have attempted using rEFInd on it.

> **tea for one said:**
> The text above is from post no.1.
As you cannot boot in EFI mode, did you make this "already-setup installation" on a different PC?
Swapping Ubuntu disks between PCs is often successful if there is no esoteric hardware involved.

I created the installation in VirtualBox and I verified that it also works on my laptop.

---

### Post by Melab on 2024-02-19
> **oldfred said:**
> You have some other issue.

I have used a grub BIOS boot stanza on old HDD to boot my UEFI install on external SSD.

So once grub had started loading boot stanza you have booted grub in UEFI mode. 
Then it really does not matter if UEFI or BIOS as you load kernel & drivers to finish boot.

No, I think the issue is with EFI booting because, as I've said, it works in BIOS mode.

I don't know what you mean by a "BIOS boot stanza". Could you clarify? To my understanding, a boot target either runs in UEFI mode or BIOS mode, and you can't switch modes while the computer is running. But, that isn't likely to solve it because this problem isn't limited to when I use GRUB to try to boot Linux. The same result happens when I try to use rEFInd as the bootloader, too.

---

### Post by Melab on 2024-02-19
So far, this conversation has touched on the bootloader that I use. Are there any kernel boot options/parameters that I might be able to use instead?

---

### Post by tea for one on 2024-02-19
> **Melab said:**
> My installation is already on a portable USB, not an internal SSD/HDD, and I have attempted using rEFInd on it.
I created the installation in VirtualBox and I verified that it also works on my laptop.
This is new information.
> **Melab said:**
> How does it know what the target root device is? Or which initramfs to use?
rEFInd will boot the kernel of a UEFI installation on an external usb device.
You simply have to choose the correct disk.

If the UEFI firmware, PC hardware and the installed OS are in good order, then it will boot.

---

### Post by Melab on 2024-02-19
> **tea for one said:**
> This is new information.

rEFInd will boot the kernel of a UEFI installation on an external usb device.
You simply have to choose the correct disk.

If the UEFI firmware, PC hardware and the installed OS are in good order, then it will boot.

Okay, so that is how it would work. But, as I've said, I have tried rEFInd before and I get *the exact same result as with GRUB*&#8203;.

---

### Post by tea for one on 2024-02-19
> **Melab said:**
> Okay, so that is how it would work. But, as I've said, I have tried rEFInd before and I get *the exact same result as with GRUB*&#8203;.
Previously, you mentioned that you can boot this external installation in Legacy (BIOS) mode on your Fit-PC3.
Can you boot the OS in BIOS mode and supply a boot-repair report?
More info [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) - 2nd option using your installed system.

It may provide a clue...............?

---

### Post by Melab on 2024-02-19
> **tea for one said:**
> Previously, you mentioned that you can boot this external installation in Legacy (BIOS) mode on your Fit-PC3.
Can you boot the OS in BIOS mode and supply a boot-repair report?
More info [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) - 2nd option using your installed system.

It may provide a clue...............?

Is this on/in the installer environment? What exactly does it do or report on? How would running this in BIOS mode even help when I'm trying to get EFI mode to work?

If this is in the installer environment, then I'll try it. But, I really think trying different kernel boot options/parameters might be the way to go instead. Do you know any that might work/help?

---

### Post by Melab on 2024-02-19
I added the following boot options to the kernel command line and booted Linux on my fit-PC3 in EFI mode:
```
earlyprintk ignore_loglevel initcall_debug earlycon=efifb
```

For the first time, I am seeing output from Linux. The kernel console output stopped with these last two lines:
```

[    8.352123] printk: console [tty0] enabled
[    8.412484] printk: bootconsole [efifb0] disabled

```

Does anyone know why this is?

---

### Post by Melab on 2024-02-21
Are there any boot options that might fix this?

---

### Post by dragonfly41 on 2024-02-21
Has anybody suggested installing efibootmgr and running in terminal?

---

### Post by Melab on 2024-02-21
> **dragonfly41 said:**
> Has anybody suggested installing efibootmgr and running in terminal?

Doing that presupposes that I have successfully booted Linux in EFI mode.

---

### Post by Melab on 2024-02-21
> **tea for one said:**
> Previously, you mentioned that you can boot this external installation in Legacy (BIOS) mode on your Fit-PC3.
Can you boot the OS in BIOS mode and supply a boot-repair report?
More info [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) - 2nd option using your installed system.

It may provide a clue...............?

What would this report if I run it in BIOS mode?

---

### Post by Melab on 2024-02-24
> **tea for one said:**
> Previously, you mentioned that you can boot this external installation in Legacy (BIOS) mode on your Fit-PC3.
Can you boot the OS in BIOS mode and supply a boot-repair report?
More info [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) - 2nd option using your installed system.

It may provide a clue...............?

**tea for one**, do you want me to run it on my fit-PC3 specifically?

---

### Post by Melab on 2024-02-24
I tried adding "nosmp" to the extra boot arguments in this post and got the same results:
> **Melab said:**
> I added the following boot options to the kernel command line and booted Linux on my fit-PC3 in EFI mode:
```
earlyprintk ignore_loglevel initcall_debug earlycon=efifb
```

For the first time, I am seeing output from Linux. The kernel console output stopped with these last two lines:
```

[    8.352123] printk: console [tty0] enabled
[    8.412484] printk: bootconsole [efifb0] disabled

```

Does anyone know why this is?

---

### Post by Melab on 2024-03-01
Does no one have any advice?

---

### Post by yancek on 2024-03-01
In post 29, you say:  "Doing that presupposes that I have successfully booted Linux in EFI mode" in response to a suggestion to run efibootmgr.  Possibly because in post 26 you say " I added the following boot options to the kernel command line and booted Linux on my fit-PC3 in EFI mode".  So did you boot in EFI mode or not?  Running the boot repair script using the 2nd option when booted from whatever you have and selecting the Create BootInfo Summar option will give details on your system and boot files regardless of whether it is a Legacy or EFI install.

> 8.412484] printk: bootconsole [efifb0] disabled 

The error above which you report in an earlier post is discussed at the kernel.org web site at the link below.  I don't know if it will help as it discusses Macs and I know nothing about them nor am I familiar with the hardware you are using.  I expect the only possibility to get real help is if you can post a link to the boot repair output.

[https://docs.kernel.org/fb/efifb.html](https://docs.kernel.org/fb/efifb.html)

---

### Post by Melab on 2024-03-02
> **yancek said:**
> In post 29, you say:  "Doing that presupposes that I have successfully booted Linux in EFI mode" in response to a suggestion to run efibootmgr.  Possibly because in post 26 you say " I added the following boot options to the kernel command line and booted Linux on my fit-PC3 in EFI mode".  So did you boot in EFI mode or not?  Running the boot repair script using the 2nd option when booted from whatever you have and selecting the Create BootInfo Summar option will give details on your system and boot files regardless of whether it is a Legacy or EFI install.



The error above which you report in an earlier post is discussed at the kernel.org web site at the link below.  I don't know if it will help as it discusses Macs and I know nothing about them nor am I familiar with the hardware you are using.  I expect the only possibility to get real help is if you can post a link to the boot repair output.

[https://docs.kernel.org/fb/efifb.html](https://docs.kernel.org/fb/efifb.html)

I added those boot options by using GRUB's menu entry edit function. GRUB works just fine.

I have been able to boot the Linux installation on my USB stick in on other platforms in EFI mode.

---

### Post by Melab on 2024-03-05
> **tea for one said:**
> Previously, you mentioned that you can boot this external installation in Legacy (BIOS) mode on your Fit-PC3.
Can you boot the OS in BIOS mode and supply a boot-repair report?
More info [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) - 2nd option using your installed system.

It may provide a clue...............?

I have attached the resulting summary.

---

### Post by oldfred on 2024-03-05
Please use Boot-Repair's option to post to a pastebin site & then post link.

Many will not download an unknown file as it may contain a virus.

---

### Post by Melab on 2024-03-08
> **tea for one said:**
> Previously, you mentioned that you can boot this external installation in Legacy (BIOS) mode on your Fit-PC3.
Can you boot the OS in BIOS mode and supply a boot-repair report?
More info [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) - 2nd option using your installed system.

It may provide a clue...............?

The boot info summary (the same one I attached in the form of a ZIP file) can be found [here]("https://pastebin.ubuntu.com/p/N2syFsDB2Z/").

---

### Post by Melab on 2024-03-08
> **oldfred said:**
> Please use Boot-Repair's option to post to a pastebin site & then post link.

Many will not download an unknown file as it may contain a virus.

Weird. Okay. I have posted it [here]("https://pastebin.ubuntu.com/p/N2syFsDB2Z/").

---

### Post by oldfred on 2024-03-08
Is sda the external drive?
Many systems promote an external drive on reboot to first drive when it is second drive when first plugged in.
You show Windows UEFI boot on sdb.

You show both UEFI & BIOS boot configuration. Often after updates only one or the other works.
And then system UEFI/BIOS has to be set to match boot mode. Some newer systems will auto switch to correct mode if you select UEFI menu entry with other boot mode. Older systems required modes matched.

Your fstab shows mount of /boot and ESP - efi system partition, so last install of grub was in UEFI mode. So always boot in UEFI mode.
But report did not show this which it normally does.
sudo efibootmgr -v

But if you can boot to grub menu, not a boot issue, but something after grub.
In grub menu remove quiet splash to see boot process. Often last line is not issue, but something before that.
> /vmlinuz-5.15.0-91-generic root=UUID=2f30d5e3-4fbe-4f2b-af8c-b81a2737a2a3 ro [COLOR=#ff0000]splash quiet[/COLOR]

While I have used rEFInd for emergency boot, I have never configured it for my system. It seems to add a lot of files into ESP. 

Do you always have external drive plugged in?
UEFI usually removes or changes an entry for any drive that is removed.
So if you have an "ubuntu" entry like an internal drive install, it then stops working. But you should always be able to boot external drive using UEFI boot menu & drive entry like when you boot the live installer. Entry actually is the /EFI/Boot/bootx64.efi. But with full installs the /EFI/ubuntu folder must exist in ESP for it to work. Some in the full install's version of bootx64.efi is hard coded to only use /EFI/ubuntu/grub.cfg.

---

### Post by Melab on 2024-11-10
> **oldfred said:**
> Is sda the external drive?

Yes, and it's the drive on which Linux resides that I have been trying to boot in UEFI mode.

> **oldfred said:**
> Many systems promote an external drive on reboot to first drive when it is second drive when first plugged in.
You show Windows UEFI boot on sdb.

Ignore the Windows drive. It's irrelevant.

> **oldfred said:**
> You show both UEFI & BIOS boot configuration. Often after updates only one or the other works.

Updates have nothing to do with this. My USB is setup so it can boot with both UEFI and BIOS. But this isn't relevant.

> **oldfred said:**
> And then system UEFI/BIOS has to be set to match boot mode.

This distinction makes no sense to me. UEFI/BIOS settings literally IS where the boot mode is selected.

> **oldfred said:**
> So always boot in UEFI mode.
But report did not show this which it normally does.
sudo efibootmgr -v

I've said ad nauseum that I CANNOT use efibootmgr on my fit-PC3 and that I CANNOT boot Linux in UEFI mode on it (I actually can, but see a few paragraphs below for clarification). If I could, then I would be in Linux, and if I was in Linux, then I wouldn't be having this trouble.

> **oldfred said:**
> But if you can boot to grub menu, not a boot issue, but something after grub.

That's what I've been trying to say.

> **oldfred said:**
> In grub menu remove quiet splash to see boot process. Often last line is not issue, but something before that.

Please see [this post](https://ubuntuforums.org/showthread.php?t=2495233&page=3&p=14180008#post14180008) to see where the result of using debugging arguments.

Now, I *can* get Linux to boot in UEFI mode *if* I add "noefi", but this makes it so that the UEFI facilities are not accessible within Linux, which is *not* what I want.

> **oldfred said:**
> Do you always have external drive plugged in?

I don't understand why you're asking these questions about the external drive. The external drive is a USB drive and it is the drive containing the Linux installation that I have been trying to boot.

> **oldfred said:**
> UEFI usually removes or changes an entry for any drive that is removed.

Not relevant. I've been selecting the boot drive manually each time.

---

### Post by Melab on 2024-11-10
> **yancek said:**
> In post 29, you say:  "Doing that presupposes that I have successfully booted Linux in EFI mode" in response to a suggestion to run efibootmgr.  Possibly because in post 26 you say " I added the following boot options to the kernel command line and booted Linux on my fit-PC3 in EFI mode".  So did you boot in EFI mode or not?

It didn't boot *successfully*, i.e., *completely*.

---

### Post by oldfred on 2024-11-10
External drives boot from the UEFI/BIOS one time boot menu, just like you boot live installer to do an install.
In UEFI/BIOS one time boot menu with newer UEFI systems you should have both a UEFI boot entry, if external drive configured for UEFI and/or a BIOS boot entry if MBR has boot code.
Some systems just have entries that say UEFI:xxx or xxx where xxx is the BIOS boot. The xxx is name or label of external drive.
Others may have two menus, a UEFI section & a BIOS section.
Not familiar with your system.

Can you boot live installer in UEFI mode?

---

### Post by Melab on 2024-11-10
> **oldfred said:**
> External drives boot from the UEFI/BIOS one time boot menu, just like you boot live installer to do an install.
In UEFI/BIOS one time boot menu with newer UEFI systems you should have both a UEFI boot entry, if external drive configured for UEFI and/or a BIOS boot entry if MBR has boot code.
Some systems just have entries that say UEFI:xxx or xxx where xxx is the BIOS boot. The xxx is name or label of external drive.
Others may have two menus, a UEFI section & a BIOS section.
Not familiar with your system.

Can you boot live installer in UEFI mode?

None of that is relevant here. No, I cannot boot Ubuntu's installer in UEFI, but, again, I select which drive to boot from, not the system—**no auto booting is used**. Furthermore, we've already established that GRUB2 works fine, meaning *that the problem is not with the boot selection screen provided by the UEFI/BIOS*.

---

### Post by oldfred on 2024-11-11
Do not know much about Tiano, but years ago I thought it was a way to UEFI boot on a BIOS only system.
[https://www.tianocore.org/about.html](https://www.tianocore.org/about.html)

---

### Post by dragonfly41 on 2024-11-11
This is a long thread. Based on OP hunch (post #1) that this is a fit-PC3 issue I queried this in Google.

**fit-PC3 EFI boot problem**

A number of suggestions pop up.

---

### Post by Melab on 2024-11-24
> **oldfred said:**
> Do not know much about Tiano, but years ago I thought it was a way to UEFI boot on a BIOS only system.
[https://www.tianocore.org/about.html](https://www.tianocore.org/about.html)

Cool. Do you know of ANY boot arguments that might help?

---

### Post by Melab on 2024-11-24
> **dragonfly41 said:**
> This is a long thread. Based on OP hunch (post #1) that this is a fit-PC3 issue I queried this in Google.

**fit-PC3 EFI boot problem**

A number of suggestions pop up.

I wouldn't be asking for help here if Google had helped.

---

### Post by dragonfly41 on 2024-11-25
So .. you have tried this suggestion gleaned from basic Google Search? ..

[COLOR=#001D35][FONT=&amp]**Reset the BIOS**[/FONT][/COLOR]
[FONT=&amp]Turn off the computer and unplug the power cable. Open the service door and remove the RAM memory modules. Short the test points TP136 and TP137 for three seconds to reset the BIOS. Reinstall the RAM and storage, close the service door, and plug in the power.[/FONT]

---

### Post by Melab on 2024-12-06
> **dragonfly41 said:**
> So .. you have tried this suggestion gleaned from basic Google Search? ..

[COLOR=#001D35][FONT=&amp]**Reset the BIOS**[/FONT][/COLOR]
[FONT=&amp]Turn off the computer and unplug the power cable. Open the service door and remove the RAM memory modules. Short the test points TP136 and TP137 for three seconds to reset the BIOS. Reinstall the RAM and storage, close the service door, and plug in the power.[/FONT]

1. I'm not going to mess with the hardware. I don't feel like risking anything.
2. I don't have a way to backup my BIOS settings, so I'm not going to throw away my settings on it.
3. I've reset the BIOS before and it didn't help.
4. I've been focusing on Linux and potential boot arguments.

---

### Post by Melab on 2024-12-06
People, PLEASE. It is NOT any of the bootloaders (e.g., GRUB2, rEFInd, etc.) & I refuse to try any others, I am NOT using autobooting, the internal/external status of the drive is irrelevant, and stop recommending efibootmgr because all that tells me is you can't comprehend what I am unable to do.

What boot arguments could I use to resolve this problem? Are similar error messages occurring on other platforms and, if so, do they have patches for it? Etc.

---

### Post by dragonfly41 on 2024-12-07
Forgive me throwing ideas into the ring but I have not followed this entire thread. Too long.
Just one obvious question. Have you set boot flags using GParted? All I can think of. If you had Windows I would suggest trying (in free trial period of 15 days) EasyUEFI just to get a different perspective since you have been turned off rEFInd, efibootmgr for reasons I don't understand because of your platform.

---

### Post by Melab on 2024-12-10
> **dragonfly41 said:**
> you have been turned off rEFInd

Because I have stared up front that rEFInd doesn't make a difference.

> **dragonfly41 said:**
> efibootmgr for reasons I don't understand because of your platform.

Pause for a minute. efibootmgr is a Linux program. In order to be usable, Linux must be mode into UEFI. Pray tell, how do imagine I might use efibootmgr when I am *unable to boot into Linux in UEFI mode in the first place*?

---

