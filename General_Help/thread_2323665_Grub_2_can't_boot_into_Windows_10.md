---
title: "Grub 2 can't boot into Windows 10"
date: 2016-05-07
forum: General Help
---

### Post by microspam on 2016-05-07
I recently installed the latest version of Ubuntu, and everything was fine.

I was messing around, and then I wanted to get back into Windows. I restarted the PC, and it went to the Grub boot loader screen.
I tell it to boot into Windows 10, and it just loads back to the Grub boot menu. It essentially loops back to the Grub boot loader screen when I want it to boot into Windows, yet it loads Ubuntu just fine.

I keep Ubuntu on an entirely separate drive from my Windows install, so it can't be an overwritten partition. :/

---

### Post by oldfred on 2016-05-07
Was Windows hibernated or UEFI Secure Boot on?
Grub only boots working Windows or Windows that is not hibernated nor needs chkdsk.
And Windows 8 or later's fast start up is always on hibernation.

Can you directly boot Windows, not thru grub.
If BIOS boot Windows hard drive. If UEFI boot Windows entry in UEFI.
Either way you should have a one time boot key like f10 or 12 to choose system/drive.

If not:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by microspam on 2016-05-07
UEFI is completely disabled. I used EasyBCD to make the Grub boot loader the default boot option.

---

### Post by microspam on 2016-05-07
[http://paste2.org/V8K7DCvy](http://paste2.org/V8K7DCvy)

Here is the boot-info url if anyone needs it.

---

### Post by oldfred on 2016-05-07
You probably changed BIOS to boot directly from grub in sdb. That would be the only way you get grub directly.
You then need to change BIOS to boot from sda.

It is my understanding the EasyBCD uses the very old grub4dos to chain to another install of grub or grub2. But with EasyBCD you are booting into Windows and EasyBCD adds entry to BCD to load grub4dos.

---

### Post by microspam on 2016-05-07
Well, how do I change the BIOS to reboot from SDA? :/

---

### Post by Cavsfan on 2016-05-07
> **microspam said:**
> Well, how do I change the BIOS to reboot from SDA? :/

You should be able to get into BIOS by pressing the delete key at bootup. 
You want to press it several times right when it starts to bootup and that should take you to BIOS.

---

### Post by microspam on 2016-05-07
I know how to bring up the BIOS screen. I want to know how I change the boot to SDA.

---

### Post by yancek on 2016-05-07
You should have a boot tab in the BIOS and options to select a specific hard drive for boot priority so change to whichever drive is sda and save the changes.

---

### Post by microspam on 2016-05-07
It's nothing to do with the boot order. It's a problem with Grub 2.

---

### Post by oldfred on 2016-05-07
You have Windows boot loader in sda, and grub only in sda per report, unless you changed it since.

Grub should still boot Windows, but again it only boots working Windows.

You change boot order in UEFI/BIOS. Typically a boot tab that shows boot entries or drives and you can move/change which entry is first.
Most systems also can  boot  using f10 or f12 which is the same as the boot tab in BIOS but directly to boot entries. You use that more for occasionly boot of a different drive like a flash drive or DVD. But since you have two drives should be able to chose either sda or sdb. If new UEFI system names may not be as clear. 

What brand/model system?
If still issues, use camera and show us screenshot of boot tab in BIOS. You can easily attach with Forum's advanced editor and paperclip icon.

Several typical boot tab screens shown, one new UEFI and a couple old BIOS. But every brand is different in details.

---

### Post by Cavsfan on 2016-05-07
On my 7 year old pc this is how in my BIOS I get to Boot Sequence, which is what you are looking for.

[ATTACH=CONFIG]268903[/ATTACH][ATTACH=CONFIG]268904[/ATTACH][ATTACH=CONFIG]268905[/ATTACH]

---

### Post by microspam on 2016-05-07
I am using a custom built PC. I've tried everything, such as using the Windows 10 installation CD, and Bootrec. Even with Fixmbr, it isn't removing grub. :/ I'm out of ideas.

---

### Post by microspam on 2016-05-07
Hopefully, this post will have an attachment of my BIOS screen.

---

### Post by oldfred on 2016-05-07
That only shows SSD which was sda and your Windows in Report. That would say you can only boot Windows.
If you somehow deleted the Windows entry with EasyBCD, then maybe it only uses grub4dos to chain to grub in sdb. 
Check BCD entries with EasyBCD or your Windows repairCD or flash drive.

But BIOS should also show drive that is sdb as it is bootable.

---

### Post by microspam on 2016-05-08
I can't check my EasyBCD entries because I can't boot into Windows in the first place. I'm also sure that I didn't delete the Windows entry, I made Grub the default loader.

---

### Post by oldfred on 2016-05-08
I do not know EasyBCD, but it has its own ISO for repairs.

But you should be able to use Boot-Repair to temporarily reinstall a Windows boot loader to the MBR of the one drive your system seems to see. Or your Windows repair disk.
From either Windows repair disk or EasyBCD repair tools on its ISO you may be able to fix Windows.

Since you have the separate Boot partition in sda1, the Windows f8 to get into its repair console should work if you are booting thru Windows, but have to do that before grub starts to load.

If really booting grub from sdb, then I do not know why BIOS is not seeing sda. That often can be a bigger issue of hard drive failure. In Ubuntu you can check drive using Disks and icon in upper right choose Smart Data. It should say drive is ok and can run tests.

---

