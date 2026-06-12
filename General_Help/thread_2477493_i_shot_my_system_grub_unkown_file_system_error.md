---
title: "i shot my system: grub unkown file system error"
date: 2022-07-27
forum: General Help
---

### Post by 0xde4dbeef on 2022-07-27
[COLOR=#232629][FONT=-apple-system]So today I have installed zoneminder on my ubuntu server laptop. It an elderly i5 wiht 8gb run and an 128gb ssd that runs ubuntu 20 lts and drives all my iot stuff. 
I have also connected and formatted an external ssd to store my recordings. I am rather sure I did not accidentally format my main drive that runs the os, but at this point I am unable to rule it out. I am quite far from a linux expert, but I did come along rather well with it so far. But sometimes it causes severe headache.
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I got zoneminder running but I did not finish configuration as I had other more important things to do. The machine kept running fine for quite some hours after that, and then suddenly one service (zigbee2mqtt) stopped working, but there was no error, home assistant kept going just fine, but it took notice that z2m was not available. I checked the log file of that component and the log file was there and there were no errors in the log file. I tried restarting the service, but it still wasn't working. So I shrugged it off and issued a reboot command. This is where the big problem started.
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]After reboot I get a "grub unkown file system" error and a "grub-rescue>" prompt. When I type ls and then try another ls on each partitions returned, all I get is unkown filesystem for every partition, which naturally worries me.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
I have now set up a live-usb and have run boot-repair which was suggested by one guide ([https://phoenixnap.com/kb/grub-rescue](https://phoenixnap.com/kb/grub-rescue)), but unfortunately it wouldn't offer me a repair, but only to paste it's results so I can ask other people for help.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Well here I am, this is the paste from boot-repair [https://pastebin.ubuntu.com/p/wskWsPYSzc/](https://pastebin.ubuntu.com/p/wskWsPYSzc/)
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]The contents of that paste are quite a bit over my head. I have no real clue what went wrong, but given the fact that the system did not immediately fail after I formatted the external drive and that the log files of z2m were accessible before the reboot I have some hope that I did not accidentally format the main drive without noticing.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
But what else did I mess up, and more importantly, how can I fix it? You help is much appreciated!
thank you![/FONT][/COLOR]

---

### Post by tea for one on 2022-07-27
> **0xde4dbeef said:**
>  I am rather sure I did not accidentally format my main drive that runs the os, but at this point I am unable to rule it out. 
[COLOR="#0000FF"]Line 33[/COLOR] - 0 OS detected

Boot-repair reports that there is no operating system on the PC

---

### Post by 0xde4dbeef on 2022-07-27
would my system keep running for hours after I format the main ssd? I'd figure it would stop working right away? Also, I formatted the external drive as ext4, but /dev/sda still shows up as lvm in testdisk. 

if I did, I've created a dd snapshopt and have been trying to run testdisk on the image. it finds the lvm partition but when I try to access the partition that's supposed to have the data on it, it reports a damaged file system. 

any ideas how I could proceed from here?

thanks!

---

### Post by MAFoElffen on 2022-07-27
No it doesn't show that there is no OS on the "drives" Just not on /dev/sda, which he said he installed a new drive...

Currently /dev/sda is the new drive, and /dev/sdb is the original drive with both Windows and Linux OS'es. You see that right? That is what I see. (Just another set of eyes.) 

Easiest idea- Swap your SATA cables on the two drives and try it... Your original drive should be assigned as /dev/sda, not /dev/sdb, because that didn't exist before you installed that new drive. Why? Because HP and Windows likes to boot from the first drive... (And some HP only look for the EFI directory on the first drive.)

If not, then switch it back and when it boots, go into the EFI BIOS settings and set the boot drive to the 'correct' drive.

---

### Post by 0xde4dbeef on 2022-07-27
> **MAFoElffen said:**
> Currently /dev/sda is the new drive, and /dev/sdb is the original drive with both Windows and Linux OS'es. You see that right? That is what I see. (Just another set of eyes.) 

Easiest idea- Swap your SATA cables on the two drives and try it... Your original drive should be assigned as /dev/sda, not /dev/sdb, because that didn't exist before you installed that new drive. Why? Because HP and Windows likes to boot from the first drive... (And some HP only look for the EFI directory on the first drive.)


this is what I initially thought when I realized the drive was still plugged when I rebooted, so I disconnected the new drive and rebooted with the same result. It is a HP laptop indeed and all I can select is the internal hd for booting. Also /dev/sda in the boot-repair paste is indeed the main drive, the usb drive running the live ubuntu is /dev/sdb. 
I really wish it was this simple. 

What I find weird is that even testdisk reports the file system of the ext4 drive inside the lvm, that's supposed to contain the data as a damaged file system. fsck exits fine when run it against /dev/sda

---

### Post by 0xde4dbeef on 2022-07-27
hmm, if I'd assume it is really just a drive mapping mismatch, this would mean I should at least be able to mount the drive on the live-usb, right? so far I was not successful doing this, what would be "the correct way" of doing this?

Edit: I've been following this guide: [https://www.cyberciti.biz/faq/linux-mount-an-lvm-volume-partition-command/](https://www.cyberciti.biz/faq/linux-mount-an-lvm-volume-partition-command/)
and it errs out with "wrong fs type, bad option, bad superblock on /dev/mapper/ubuntu--vg-root, missing codepage or helper program, or other error."

I've made a dd image of the drive just in cas but I think it's time to just start reinstalling the system, i've spent half a day trying to google fixes. I didn't even come across anyone having a similar problem like mine ...

---

### Post by tea for one on 2022-07-27
> **MAFoElffen said:**
> Currently /dev/sda is the new drive, and /dev/sdb is the original drive with both Windows and Linux OS'es. You see that right? That is what I see. (Just another set of eyes.) 
[COLOR="#0000FF"]Line 96[/COLOR] - sdb:31.6GB:scsi:512:512:gpt:JetFlash Transcend 32GB

I thought that sdb was the live system using a USB device.
[COLOR="#0000FF"]Line 112[/COLOR] indicates that sdb has a filesystem iso9660

---

### Post by oldfred on 2022-07-27
You have mixed UEFI & BIOS boot.
You have grub in MBR and UEFI shows 'ubuntu' boot entries, but no ESP - efi system partition.
The GUID/partUUID of ESP in UEFI, does not exist.
And since grub in MBR seems to find boot files in LVM, it looks like you have BIOS/CSM/legacy boot configured.
You did boot live installer in UEFI boot mode.

Did you change boot modes? You need to be booting in BIOS mode.

The way Linux updates system is that old kernel keeps running when new one is installed. Then on reboot the new one is loaded.
So you can have system keep running as kernel is still in RAM, but if everything deleted, you would start to get errors on anything that was not in RAM. Many things are cached in RAM, so system may work for a while.

---

### Post by 0xde4dbeef on 2022-07-28
I have indeed managed to boot the system in legacy mode from the usb and try boot-repair again, and the result was exactly the same. 

I have tried to fix the system for a full day with absolutely zero success, and eventually decided it would have been less time to set up the system again from scratch, so I wiped the disk clean and reinstalled ubuntu and started reconfiguring everything from scratch. 

I'd still love to know what went wrong. The system was in production use for 2 years. I did have other external drives attached and it never refused reading the file system. In my simple head it wouldn't make sense why running the system from legacy bios instead of uefi would suddenly cause a major problem?
I do still have a dd dump of the entire drive.

---

### Post by oldfred on 2022-07-28
You need to always be in UEFI mode or BIOS mode.
Updates to UEFI firmware may reset UEFI settings back to defaults. Which may turn on UEFI Secure Boot, preventing BIOS boot.
But even if UEFI boot, you may need to turn Secure Boot off.

Since hardware has been UEFI for 10 years better to use gpt partitioning & UEFI boot mode.
You can use gpt with old BIOS, and really should only use MBR(msdos) if you must boot Windows in old BIOS mode.

If system not correctly shutdown or power failure, you often have to run file system checks. If ext4, you use fsck or e2fsck to repair file system.
If drive is failing, then a bigger issue. You can check drive status with Disks and icon in upper right for SmartStatus or use smartmon tools.

---

### Post by 0xde4dbeef on 2022-07-30
> **oldfred said:**
> You need to always be in UEFI mode or BIOS mode.
Updates to UEFI firmware may reset UEFI settings back to defaults. Which may turn on UEFI Secure Boot, preventing BIOS boot.
But even if UEFI boot, you may need to turn Secure Boot off.

So let's assume UEFI vs. BIOS was the root cause why grub reported a file system error, I then should have been able to just mount the drive in live-usb and access the data, right? which wasn't the case. 


> **oldfred said:**
> If system not correctly shutdown or power failure, you often have to run file system checks. If ext4, you use fsck or e2fsck to repair file system.
If drive is failing, then a bigger issue. You can check drive status with Disks and icon in upper right for SmartStatus or use smartmon tools.

fsck actually did not report any errors when I ran it on the live usb. The drive is still running fine, no errors whatsoever.

---

### Post by oldfred on 2022-07-30
Standard first user is actually user 1000 inside the system. Second user is 1001 etc.
so a user name is assigned to the user number.

But live installer is user 999 which then will give issues with any default type mounts as you are then not the owner.

---

### Post by 0xde4dbeef on 2022-08-01
> **oldfred said:**
> Standard first user is actually user 1000 inside the system. Second user is 1001 etc.
so a user name is assigned to the user number.

But live installer is user 999 which then will give issues with any default type mounts as you are then not the owner.

wait, am I getting this right? If I try to mount a filesystem from the wrong user number I would actually get a file system error instead of a permissions error when I try to mount a drive?

---

### Post by oldfred on 2022-08-01
Are you mounting with sudo?
I have not used live installer in live mode for ages, but sudo should work, and Ubuntu does not have a password for live installer. Other distributions may have user & password on live installer in live mode.
Its just if using gui apps they open with defaults.

When user "other", you may not have permissions.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

