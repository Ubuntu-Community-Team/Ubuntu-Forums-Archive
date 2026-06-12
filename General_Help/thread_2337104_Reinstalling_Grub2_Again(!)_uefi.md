---
title: "Reinstalling Grub2 Again(!) uefi"
date: 2016-09-14
forum: General Help
---

### Post by Quarkrad on 2016-09-14
I've done this before (a few times) but this time I'm having trouble.  Installed win10 on gpt disk followed by 16.04 - all went OK after installing 16.04 - rebooted and presented with grub screen, selected ubuntu and got to Desktop.   Restarted and pc booted straight into win10 (no grub) - restarted again and booted straight to win10.  Checked in bios and order of boot is 1st ubuntu 2nd windows boot manager.  Repeated reboots always into win10 - no grub screen.   Inserted live cd and used following commands:

```
sudo mount /dev/sd*** /mnt
sudo mount /dev/sd** /mnt/boot/efi
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
grub-install /dev/sd*
update-grub  
```

This worked OK - I rebooted and was presented with the grub screen, chose ubuntu and went to Desktop.  I restarted and pc booted directly into win10 - no grub screen(?).  One thing I did notice that maybe relevant - in my bios (gigabyte) I can alter the boot preferences but when I press f10 to save there is a summary of the boot order.   The order is as I changed but lower down the page there is a list called Boot Override that has Windows Boot Manager first and then Ubuntu.  Things is - I cannot find anything in my bios to do with Boot Override.

---

### Post by oldfred on 2016-09-14
What model Gigabyte?
Do you have latest UEFI from Gigabyte?
Do you have Secure boot on?
Do you have fast boot in UEFI on?

My Gigabyte Z170 only boots Ubuntu, so I do not have any dual boot issues. But I have UEFI Secure boot off. My manual has no info on Boot-override & I am not at that computer now.

---

### Post by Quarkrad on 2016-09-14
I have H81M-DS2V   bios version F6  bios date 08/11/2015   bios id 8A03AG0Z  - which is the latest.  There is no option for secure boot but Fast Boot is disabled.  I have also turned off hibernation in win10 so when it shuts sown it really shuts down.

---

### Post by oldfred on 2016-09-14
Your manual almost looks identical to my Z170.
Your UEFI secure boot setting is "Windows" or "Other" under Windows 8 features. 
It says default is "Other". But that setting seems to turn on/off other CSM options.

Rest of UEFI settings are under CSM.

---

### Post by Quarkrad on 2016-09-14
This is what that section of the bios looks like:

```
Windows 8 Features		        Other OS
Boot Mode Selection		       UEFI and Legacy
LAN PXE Boot Option ROM		       Disabled
Storage Boot Option Control	        UEFI First
Other PCI Device ROM Priority	        UEFI OpROM
Network Stack			        Disabled
```

---

### Post by oldfred on 2016-09-14
I think that is identical to what my settings are. But will not be at that system for several weeks.

My Asus only booted with UEFI, with UEFI only everywhere.

---

### Post by Quarkrad on 2016-09-15
Thanks - we both have 'everything uefi' turned on.  However, I'm still booting to Win10 every time.  I have four boot priorities - the first two are Ubuntu and the 3rd and 4th Windows Boot Mgr.  Seems it is ignoring the ubuntu options.

---

### Post by Quarkrad on 2016-09-15
Not sure whether I am closer or further away.  I ran boot repair with a live cd session and it seems I have a locked-esp.  Details are paste.ubuntu.com/23181699 (not sure how one accesses this file).

---

### Post by Quarkrad on 2016-09-15
Looks like I've solved this using some of your commands from another thread:

sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sda2
man dosfsck 

Many thanks.

---

### Post by oldfred on 2016-09-15
Glad you got it resolved. 
Did not see that file corruption or file problems was an issue.

---

### Post by Quarkrad on 2016-09-17
The last line of my paste.com log report into why boot-repair failed said:

```
An error occurred during the repair.

Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot/efi partition:] option
```

So I followed the locked-ESP trail and came across a thread where your good self had suggested the code in #9.  I tried that code(s) and fortunately it worked - I have my system(s) back.

---

