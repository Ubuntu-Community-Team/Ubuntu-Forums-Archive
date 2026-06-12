---
title: "boot-repair unsuccessful on Ubuntu 18.04 LTS/Windows 10 dual boot"
date: 2020-08-20
forum: General Help
---

### Post by bjfcom on 2020-08-20
Hi Thanks for reading.

I have a dual-booted AMD Ryzen running Ubuntu 18.04 LTS / Windows 10

I am currently having a booting issue which has not not resolved after running boot-repair multiple times. A couple of times I have been successful at booting ubuntu after running the repair, however, after the next shutdown and reboot, I have the same issue.

This is the most recent attempt at removing and replacing Grub:
[http://paste.ubuntu.com/p/HzRfdQTVmP/](http://paste.ubuntu.com/p/HzRfdQTVmP/)

I don&#8217;t really understand what the log is telling me. It seems that Windows might be locking the drive in some way (based on googling some of the dialog).

However, at this point, running boot-repair does nothing. The options to boot Ubuntu in either normal mode or repair mode, does the same thing. It looks like it is going to boot, dumps a verbose dialog which is unreadable and then shutsdown.

At this point, I don&#8217;t really know if this is a software issue or possibly a failing drive. I ran the &#8220;check disc for defects&#8221; when I boot Ubuntu with an external USB stick. It reported no issues, but given how fast it ran, I doubt it it scanned the whole drive. Also, since the screen dialog runs by so fast, I can&#8217;t really get any sense of the issue, as well as, cannot access any Ubuntu system logs since I cannot boot.

I am hoping someone might offer a suggestion about how to fix this issue or just to determine if the drive is failing and what to do. The Windows partition seems to be fine.

I have most of the data on the drive backed-up, so I don&#8217;t mind doing a reinstall, but I&#8217;m not sure that&#8217;s necessarily wise, in particular, if there is some bad sector.

Thanks in advance for your input!

---

### Post by CelticWarrior on 2020-08-20
Have you disabled Fast Startup in Windows? You must.

---

### Post by bjfcom on 2020-08-20
Aha! That's it. I thought I had already tried this, but I must have forgotten to "save changes."

Windows strikes again.

Thanks for your help!

---

### Post by bjfcom on 2020-08-20
Actually, it worked for two boots, then stopped. I went back to the Windows partition and fastboot is indeed turned-off.

---

### Post by oldfred on 2020-08-20
Windows regularly turns fast startup back on. So you may have to regularly turn it back off.

HP is not particularly friendly with booting Ubuntu by default.

Some have reported that updating UEFI and then in UEFI change boot order so Ubuntu entry is first.
Most systems let you use efibootmgr to set boot order, which grub also uses on install. But that seems to only work for a one time reboot.

Also some have to add an ubuntu entry to Windows BCD, as some UEFI/Microsoft systems sync BCD and UEFI entries. But this may interfere with direct boot of Windows which you need to be able to turn fast start up off when Windows has turned it back on. Grub only boots working Windows and will not boot Windows if fast start up is on.
In Windows:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
If not working you can remove entry:
bcdedit /deletevalue {bootmgr} path \EFI\ubuntu\grubx64.efi

---

### Post by bjfcom on 2020-08-22
Thanks oldfred,

I guess a couple of questions. The dual boot was working fine for about 6 months, which is why I was thinking it might be a disc problem. Would this still conform to a fast boot issue?

I have repeatedly observed that the "check-mark" for fast boot is not re-checking, or turning back on. Are you suggesting that Windows will turn fast boot back on, but will not show it in it's gui?

Bios just updated a few days ago after a Windows boot, so I don't think I need to update UEFI. Can you update UEFI outside of Bios? Also, this issue was occurring prior to the Bios update, so I don't think the issue is related. I checked the UEFI boot order. I hadn't noticed this before, but Ubuntu and Windows are both listed in a sub category called "OS Boot Manager." Here Ubuntu is listed as first under the boot manager:

Something like this:
UEFI Boot Order
* USB Flash
* CD Rom
* OS Boot Manager
** Ubuntu
** Windows

I'm not sure what efibootmngr is, but I'm guessing it's the category (and sub-categories) seen above?


That leaves me with trying to change Windows BCD, which I've never done before. And I'm a little concerned with your warning: > But this may interfere with direct boot of Windows which you need to be able to turn fast start up off when Windows has turned it back on. Grub only boots working Windows and will not boot Windows if fast start up is on

If I make this entry, and cannot boot Windows, how could I delete the entry as you suggested as the step to do if things don't work. Perhaps, I guess by changing the boot order in UEFI?

Thanks again

---

### Post by oldfred on 2020-08-22
You always need the Ubuntu live installer and a Windows repair flash drive, so you can repair either system when needed.
And always need good backups, so you can re-install if drive fails, or user error causes such a major issue that re-install and restore from backup is easiest alternative.

In Ubuntu terminal:
man efibootmgr
It is a tool to edit UEFI boot entries which works for just about everyone but HP.

UEFI update may reset some settings to system defaults in UEFI. Back in BIOS (only) days all settings were always reset. My motherboard needs about 7 settings, some required and some optional for what I want, so I keep a list and normally have to redo them.

With BIOS you always updated from a downloaded file usually on a DOS bootable device. With UEFI, many update directly from UEFI reading an update file in a FAT32 formatted drive or partition, from a DOS bootable device, or from within Windows.
Some now update from within Linux systems.
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)


Most vendors first level help desk will say they do not support Linux. But if they are allowing updates from Linux, then there is some recognition that users do install Linux on their systems.
I currently only build systems, but if buying a system, I would only look at systems that allow fwupd.

---

### Post by bjfcom on 2020-08-22
Hi oldfred,

I really appreciate your effort here. I'm thinking that this is a real pain and don't really even want the Windows partition anyway. If I just deleted the partition and installed only Ubuntu, would I still run into the same booting issues.

I'm guessing I would because this is more an HP/EFI problem...

OK, I'm going to try your suggestions when I get the chance.

Thanks again.

---

### Post by CelticWarrior on 2020-08-22
My admittedly limited experience with a few HP laptops is that it takes effort to make a proper dual-boot but perfectly fine with standalone Ubuntu like the one I'm running right now to post this.

---

