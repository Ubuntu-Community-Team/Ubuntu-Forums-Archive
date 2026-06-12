---
title: "Trouble fixing grub rescue screen-dual boot"
date: 2014-08-03
forum: General Help
---

### Post by csking332 on 2014-08-03
Any help is appreciated. I've been trying to fix this for a couple days now.

Trying to dual boot win8 and ubuntu on an HP envy(15-j1063cl). Whenever I boot my computer I get the "grub rescue" screen. I can boot to either ubuntu or windows 8 by booting the right .efi file from the boot options menu.

I've run boot repair multiple times, but I still can't get past this screen. I would like to use rEFInd, and I've tried installing that as well.

Output of boot repair: [http://paste.ubuntu.com/7942689/](http://paste.ubuntu.com/7942689/)

---

### Post by oldfred on 2014-08-03
I do not know details of rEFInd, but have suggested it as one of the work arounds for HP (and some others) that only like to boot Windows. Some have reported that it works to resolve issues where HP has modified UEFI to only boot Windows.

Not sure why you get grub rescue, but still can boot from one time boot key. Usually issue is that Windows resets itself to always be first in UEFI boot menu.

       It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it many rename bootx64.efi and copy grub or shim into /efi/boot folder and name it bootx64.efi.


 Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change

 [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by csking332 on 2014-08-03
When you say /efi/boot folder, are you referring to a folder inside the ubuntu install?

Update: I renamed the file in /boot/efi/EFI/Boot as posted above. But I get the same thing

---

### Post by oldfred on 2014-08-03
With UEFI you have a separate efi partition that is FAT32 formatted.
In that partition are the efi folders and efi boot files for each system.

Typical efi partition folders:
       /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu

---

### Post by csking332 on 2014-08-03
Ah ok. How do I go about seeing those?
In the boot repair output we can see they are on /dev/sda2

---

### Post by oldfred on 2014-08-03
I do not know how to fix rEFInd, most have posted that it just works.
The author occasionally posts in askubuntu forum.

         From live installer mount the efi partition on hard drive:
    mount /dev/sda2 /mnt
    cd /mnt/efi

You also have /efi/HP and /efi/refind

If you have clicked on it with Nautilus it will be mounted under the UUID or size. You have to unmount it to remount as above.

---

### Post by csking332 on 2014-08-03
Thank you for all of your help. I was able to do the renaming on /dev/sda2, but I still get error: no such device (string of numbers/letters) then grub rescue.

---

### Post by oldfred on 2014-08-03
In your efi partition should be a grub.cfg. And it may only have three lines. The configfile line should refer to the reall grub.cfg in your install.

BootInfo report does not show that file, so we do not know if it is correct or not.
Check UUIDs and anything else it should in effect be setting root to loot for grub.cfg in your install.

A one line version is like this, but then partition has to be correct.
       configfile (hd0,gpt6)/boot/grub/grub.cfg

---

### Post by csking332 on 2014-08-12
> **oldfred said:**
> In your efi partition should be a grub.cfg. And it may only have three lines. The configfile line should refer to the reall grub.cfg in your install.

BootInfo report does not show that file, so we do not know if it is correct or not.
Check UUIDs and anything else it should in effect be setting root to loot for grub.cfg in your install.

A one line version is like this, but then partition has to be correct.
       configfile (hd0,gpt6)/boot/grub/grub.cfg

Sorry for the delay, had a little vacation. 

I have since wiped my hard drive and reinstalled Windows. I had attempted what you said but still couldn't figure it out, I think I had messed it up beyond repair. All of the UUIDs looked good but still went to grub rescue screen on boot. Thanks for your help though!

For anybody looking at how to switch to rEFInd instead of using grub,[ the answer I received from Rod Smith]("http://askubuntu.com/questions/506297/cannot-fix-grub-after-running-boot-repair"), the creator of rEFInd may, help you.

---

