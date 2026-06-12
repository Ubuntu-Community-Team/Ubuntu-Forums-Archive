---
title: "Boot Repair D:  &quot;File system repair requires to unmount partitions...&quot; loops"
date: 2017-05-26
forum: General Help
---

### Post by javierdl on 2017-05-26
Hi all,

I used to have the regular Grub2 boot loader allowing me to choose between Windows (from a HD) and Ubuntu (from a SSD). But now it only boots into Windows. 
I can only think of 2 new things that may be related:
1. Windows 10 updates.
2. I installed a utility called Ext2 Volume Manager, which allows Windows to mount a EXT4 partition.

So when I run Boot Repair Disk from a USB drive, after clicking on the top big button, it pops up a window saying: 
[B]
"File system repair requires to unmount partitions. Please close all your programs. Then close this window."

[/B]I already tried unmounting every partition I found with Gparted. But without avail :(

I found a page at Ask Ubuntu advising to get [rEFInd Boot Manager to help]("https://askubuntu.com/questions/473827/grub-issue-and-botrepair-wont-work").

What should be my next step?

Thanks guys :)

---

### Post by javierdl on 2017-05-26
I was able to boot into Ubuntu thanks to rEFInd. However, rEFInd was running from a USB drive.
Once inside Ubuntu I installed rEFInd with its PPA. Then I rebooted, and no rEFInd nor Grub2 loader showed though :( (I don't get what was the purpose of installing the rEFInd's PPA then).
So it would be nice to fix the original Grub2 loader somehow, otherwise I would have to dedicate one USB port permanently just for running rEFInd from its USB drive. Which is not exactly convenient.

Btw, could an admin change this thread's label from Lubuntu to Ubuntu? I made a mistake when choosing (rolling eyes). Thanks

---

### Post by oldfred on 2017-05-26
I have not yet tested rEFInd. Said that for years. And many say it works well.

What brand/model system?

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Some have reported that Boot-Repair only gives the pastebin site not the link to a report. 
If so copy report to a pastebin site and post that link. Usually too long to directly post to forum.

Changed to Ubuntu.

---

### Post by javierdl on 2017-05-28
Hi Oldfred!!!
So nice to hear from you :)

I am doing this from a LIVE Ubuntu USB.
I tried using the PPA to install Bootinfo, but I got this error:

> (appstreamcli:3815): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
Reading package lists... Done

Acer Predator 710, Intel® Core&#8482; i5-6400 CPU @ 2.70GHz × 4, 16Gb ram, 1x1Tb HD, 1x128Gb SSD

---

### Post by oldfred on 2017-05-28
Make sure you have latest UEFI from Acer.

Acer's have a unique requirement of setting UEFI supervisory password (never lose that or immediately reset) and enabling trust on the .efi boot files in the ESP from inside UEFI.

 Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by javierdl on 2017-05-29
I've got the Boot info working!
Here's the [report URL]("https://paste2.org/3mEadN0N/followup").

I googled the error text line I posted before: "(appstreamcli:3815): CRITICAL **: Error while moving old database out of the way."
And I found this command:
> sudo rm -rf /var/lib/apt/lists

---

### Post by javierdl on 2017-06-02
Anyone?

---

### Post by oldfred on 2017-06-02
Did you resolve error?
Did you run Boot-Repair's suggested fix of reinstall of grub?

Is UEFI set "trust" on the .efi boot files? The Acer boot requirement. Not sure if it needs refreshing on file updates.

Windows updates will always reset UEFI to make Windows first in boot order.
Reinstall of grub will also reset grub/ubuntu to first in boot order, but full reinstall not required if boot order is issue.
Your can use efibootmgr to reset boot order or most UEFI let you change which boots first from inside UEFI.

You also show the very old grub4dos and /grldr in sdc. That is usually from EasyBCD and not required with UEFI. In fact it may create more issues. Best to uninstall or delete.

Usually rEFInd works?

---

### Post by javierdl on 2017-06-02
> **oldfred said:**
> Did you resolve error?

No. Still same error. 
I installed a couple updates from Acer, but they did not have any effect on that error. I tried Boot Rep D last night, after I had installed the updates and I still get that same error.

> **oldfred said:**
> Did you run Boot-Repair's suggested fix of reinstall of grub?

Yes.

> **oldfred said:**
> Is UEFI set "trust" on the .efi boot files? The Acer boot requirement. Not sure if it needs refreshing on file updates.

Fortunately that was never an issue with my computer model. I recall having to look into that for previous issues. But my BIOS is different, it doesn't have that section where to assign those trusted efi boot files. Most importantly, it was not needed.

> **oldfred said:**
> Windows updates will always reset UEFI to make Windows first in boot order.
...

I wish it was just fixing the order. Unfortunately the problem is that Ubuntu is not in the list at all.

> **oldfred said:**
> You also show the very old grub4dos and /grldr in sdc. That is usually from EasyBCD and not required with UEFI. In fact it may create more issues. Best to uninstall or delete.

Interesting! How do I uninstall it?

> **oldfred said:**
> Usually rEFInd works?

Yes, rEFInd did work. But only from a USB drive :(

---

### Post by oldfred on 2017-06-02
Perhaps issue is this in fstab?
```
# /boot/efi was on /dev/sda1 during installation
UUID=D45B-1044  /boot/efi       vfat    umask=0077      0       1
```

One of the things Boot-Repair does is backup this file in ESP:
/EFI/Boot/bootx64.efi

But Ubuntu changed mount in Ubuntu to umask=0077 from defaults it used to use. Perhaps as a security issue so working system cannot modify boot files in ESP.
Up thru 14.04 Ubuntu used defaults. And I immediately change to defaults before rebooting after install as I have to edit & move files around in ESP.
And Boot-Repair normally changes that to defaults.
This is mine:
```
UUID=D966-440A    /boot/efi    vfat    defaults    0    1
```

If working from live installer you then have to mount the sdb6 partition and drill down to /etc/fstab. I typically use nano editor as that is always available with sudo to edit system files. 

Never used EasyBCD, not sure how to delete. Is it an entry in your Windows BCD? and these perhaps others? But in sdc, so doubt if issue with current boot problems.
    Boot files:        /menu.lst /grldr /grldr

---

### Post by javierdl on 2017-06-03
Thanks Oldfred.
So if I understood correctly, it's just a matter of gaining access to the [COLOR=#000000]sdb6 [/COLOR]fstab file, and replace the "[COLOR=#000000][FONT=&quot]umask=0077[/FONT][/COLOR]" entry to "defaults". Right?

Thanks, I'll give it a try.

---

