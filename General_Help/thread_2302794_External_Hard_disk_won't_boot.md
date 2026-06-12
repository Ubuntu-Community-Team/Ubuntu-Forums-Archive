---
title: "External Hard disk won't boot"
date: 2015-11-13
forum: General Help
---

### Post by tamkahin on 2015-11-13
i m on Ubuntu 14.04.3 LTS 64-bit now, when i go to BIOS and select my hard disk to boot from, it just jumped to my normal window 7/10, my hard disk only have ubuntu on it, it worked on all my other laptops and computer except this one :'(

---

### Post by ajgreeny on 2015-11-13
I'm lost!
What OS is on the USB external disk and what is on the internal HDD?

Is the computer on which it does not work UEFI, and all other computers MBR BIOS?

---

### Post by tamkahin on 2015-11-14
> **ajgreeny said:**
> I'm lost!
What OS is on the USB external disk and what is on the internal HDD?

Is the computer on which it does not work UEFI, and all other computers MBR BIOS?

Window 7 and 10 are on the internal HDD and Ubuntu (the version I said above) is in the USB external disk

---

### Post by ajgreeny on 2015-11-14
> **tamkahin said:**
> Window 7 and 10 are on the internal HDD and Ubuntu (the version I said above) is in the USB external disk
And the answer to my UEFI question is?

---

### Post by tamkahin on 2015-11-14
> **ajgreeny said:**
> And the answer to my UEFI question is?
Hmm don't know about this part, how do I check?

---

### Post by ajgreeny on 2015-11-15
See Boot-Repair in my signature, follow the instruction from to run the Boot-info script and post back here with the **pastebin** URL you get from that.

---

### Post by tamkahin on 2015-11-15
> **ajgreeny said:**
> See Boot-Repair in my signature, follow the instruction from to run the Boot-info script and post back here with the **pastebin** URL you get from that.

An operate system wasn't found. Try disconnect any drives that don't contain an operating system.
I dun have any other drives other than my internal HDD and USB for boot-repair and the Linux hard disk

---

### Post by tamkahin on 2015-11-15
> **tamkahin said:**
> An operate system wasn't found. Try disconnect any drives that don't contain an operating system.
I dun have any other drives other than my internal HDD and USB for boot-repair and the Linux hard disk
oh wait i haven't installed it XD

---

### Post by tamkahin on 2015-11-15
> **ajgreeny said:**
> See Boot-Repair in my signature, follow the instruction from to run the Boot-info script and post back here with the **pastebin** URL you get from that.

GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.


Boot repair URL
[http://paste.ubuntu.com/13282662/](http://paste.ubuntu.com/13282662/)

---

### Post by oldfred on 2015-11-15
You partitioned with gpt which is fine, but with gpt you need either the ESP - efi system partition for UEFI boot or a bios_grub partition for BIOS boot. 
Since Windows installs are BIOS you should keep Ubuntu as BIOS boot.

Then just as Boot-Repair says.
> 
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted
Use gparted and create a 1 or 2MB unformatted partition with the bios_grub flag. It can be anywhere on drive.

Do not run any autofix from Boot-Repair as that installs grub to all drives. I think as long as you tick that drive is removeable it does not do that. But better to use advanced mode and choose operating system and choose drive's MBR to install grub into.

---

### Post by tamkahin on 2015-11-15
> **oldfred said:**
> You partitioned with gpt which is fine, but with gpt you need either the ESP - efi system partition for UEFI boot or a bios_grub partition for BIOS boot. 
Since Windows installs are BIOS you should keep Ubuntu as BIOS boot.

Then just as Boot-Repair says.

Use gparted and create a 1 or 2MB unformatted partition with the bios_grub flag. It can be anywhere on drive.

Do not run any autofix from Boot-Repair as that installs grub to all drives. I think as long as you tick that drive is removeable it does not do that. But better to use advanced mode and choose operating system and choose drive's MBR to install grub into.

I cannot add or resize any partition of my hard disk in gpart

---

### Post by oldfred on 2015-11-15
You cannot resize partitions that are mounted, or in effect from inside your install. You have to use a live installer, and even then may have to click on swap and swap-off to unmount it.

Little key symbols show mounted partitions.

---

### Post by tamkahin on 2015-11-15
> **oldfred said:**
> You cannot resize partitions that are mounted, or in effect from inside your install. You have to use a live installer, and even then may have to click on swap and swap-off to unmount it.

Little key symbols show mounted partitions.

What do mean by using a live installer?

---

### Post by oldfred on 2015-11-15
This is the live installer, it can be used as a live system to make repairs or test that system works, and then also as an installer:
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by tamkahin on 2015-11-16
> **oldfred said:**
> You partitioned with gpt which is fine, but with gpt you need either the ESP - efi system partition for UEFI boot or a bios_grub partition for BIOS boot. 
Since Windows installs are BIOS you should keep Ubuntu as BIOS boot.

Then just as Boot-Repair says.

Use gparted and create a 1 or 2MB unformatted partition with the bios_grub flag. It can be anywhere on drive.

Do not run any autofix from Boot-Repair as that installs grub to all drives. I think as long as you tick that drive is removeable it does not do that. But better to use advanced mode and choose operating system and choose drive's MBR to install grub into.

i used gparted and create a 1 or 2MB unformatted partition with the bios_grub flag. 
But now when i try to use the boot repair it keep saying "Filesystem repair requires to unmount partitions. Please close all your programs. Then close this window."

---

### Post by oldfred on 2015-11-16
Did you force shutdown or use power switch to turn off system?
That usually causes file corruption and you have to run fsck in Linux or chkdsk in Windows.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
to see which partitions are ext formatted:
sudo parted -l
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

      
 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by tamkahin on 2015-11-16
So I need to use chksdk to check the file and fix it?

---

### Post by oldfred on 2015-11-16
For NTFS partitions you use chkdsk from a Windows repair console or from its internal repair console.

For ext formatted Linux partitions you use e2fsck from a Linux live boot system.

You cannot run chkdsk from Linux nor run any Linux repairs from Windows.

---

### Post by tamkahin on 2015-11-16
But I can't run Linux, this is the problem

---

### Post by oldfred on 2015-11-16
Then you have to boot live mode using install DVD or flash drive as posted above.

---

### Post by tamkahin on 2015-11-17
I change the filesystem of bios_grumb into cleared and do the boot repaired again and it said it succeed and the boot repaireURL [http://paste.ubuntu.com/13313744/](http://paste.ubuntu.com/13313744/)

---

### Post by tamkahin on 2015-11-17
Nope although it said fixed it still just boot into window

---

### Post by oldfred on 2015-11-17
You have to go into BIOS and set it to boot external drive first. 
Or use your one time boot key, often f10 or f12, but check your manual. That should be the same as the boot tab in BIOS, but quicker access.

---

### Post by tamkahin on 2015-11-18
> **oldfred said:**
> You have to go into BIOS and set it to boot external drive first. 
Or use your one time boot key, often f10 or f12, but check your manual. That should be the same as the boot tab in BIOS, but quicker access.
do u mean selecting the hard disk to boot in the bios
i already did that everytime i boot and boot with other external boot source i did that too but i just skips to the next system and did boot linux

---

### Post by oldfred on 2015-11-18
You show grub installed to external drive.
So BIOS should at least try to boot from it and if correctly installed then external should boot. And since Boot-Repair updated it, it should be correct.

But if you are not having BIOS boot external first or manually telling it to boot external, it will continue to boot from internal.

---

### Post by tamkahin on 2015-11-22
> **oldfred said:**
> You have to go into BIOS and set it to boot external drive first. 
Or use your one time boot key, often f10 or f12, but check your manual. That should be the same as the boot tab in BIOS, but quicker access.

Sorry for replying so late I m quite busy these days
How to set it to boot external drive first 
I think the computer that won't work the bios is the asus one

---

### Post by oldfred on 2015-11-22
Are we now discussing a different computer than the one you posted the Boot-Repair script on?

---

### Post by tamkahin on 2015-11-22
Same

---

### Post by oldfred on 2015-11-22
If it works on other computers then it is something in how you have BIOS set to boot, or if older than 10 years old system, it just may not boot from USB ports. Only a year or two after USB2 ports came out did they add USB boot (and many systems then did not have CD).

---

### Post by tamkahin on 2015-11-25
> **oldfred said:**
> If it works on other computers then it is something in how you have BIOS set to boot, or if older than 10 years old system, it just may not boot from USB ports. Only a year or two after USB2 ports came out did they add USB boot (and many systems then did not have CD).
The computer that wont work was bought within this year

---

### Post by oldfred on 2015-11-25
If a new computer you have UEFI vs. BIOS/CSM issue.

So internal drive will be UEFI, but your install to external was BIOS/CSM.
You also then have to turn off UEFI or turn on CSM/BIOS to boot external.
There may be other settings in UEFI required, such as Secure boot off, and/or turn on allow USB booting.

---

