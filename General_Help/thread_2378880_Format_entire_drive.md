---
title: "Format entire drive?"
date: 2017-11-28
forum: General Help
---

### Post by dryan775 on 2017-11-28
Hello,

My dual boot system failed and I've decided to wipe the entire drive and be RID of Windows.
I have booted the laptop into a Live session (Ubuntu GNOME 16.04.2 LTS) from a USB toram and seems to be working fine as such.

I tried to run the "Install Ubuntu" from the desktop.
After hitting the very first question, the cursor starts to spin.  Goes on for a LONG LONG time.
The first time it did this it finally did come back and say there were other OS installed on a BIOS system, currently booted as EUFI and if I wanted to be able to boot into the other OS, not to proceed.
I told it I was OK with wipring the BIOS OS (since i want to wipe the entire drive), but the cursor just went back to spinning for a LONG time.

I tried loading the Disks utility, I can see all the partitions I want to get rid of, but it won't let me do anything.  Just spins and spins.

Any ideas how to force this to reformat the drive?

Thanks,
   DwR

---

### Post by oldfred on 2017-11-28
UEFI or BIOS install/system?
Better to use latest 16.04.3.

I have two drives & lots of partitions and it takes a while.
But if you have any partition type issues, it may spin forever.

Have you tried gparted. and/or gdisk if you want UEFI.
If you want BIOS but but will never install Windows on drive, you can use gpt. Ubuntu will boot from gpt with BIOS, but Windows only boots from gpt with UEFI.

If you want UEFI, recreate drive as gpt, if you want BIOS make sure MBR.

---

### Post by dryan775 on 2017-11-28
I tried sudo gparted, it launched a GUI for Libparted.  That tried to scan the drive and came back "Input/Output Error during Read on /dev/sda"

If I check in Disks, it shows /dev/sda is an small 134MB partition, unallocated space
Retry Cancel Ignore  Ignore just pops up the same message, retry does also after a longer interval.

I can't seem to get any further with gparted.

gdisk seems to work, but not sure what I'm doing.  I didn't see an option to format entire drive in the help notes

---

### Post by dryan775 on 2017-11-28
OK, I messed around with gdisk.  I think partition 8 was ausing the problem.  Once I got it cleared gparted was able to see the entire disk.  I think is' formating now...

---

### Post by SeijiSensei on 2017-11-28
You can always format filesystems from the command prompt with mkfs.  For instance,
```
sudo mkfs -t ext4 /dev/sda1
```
creates an EXT4 filesystem in the first partition on /dev/sda.  To format the entire drive, you would need to use a partitioner like gparted or fdisk to create a single partition that spans the entire device.  Then use the command above with the appropriate identifier for the device like /dev/sdb1, /dev/sdc1, etc., depending on where the device is mounted.

---

### Post by leunam12 on 2017-11-28
Input/output errors are usually an indication that the drive is going bad. Have you checked the SMART data with the Disks utility?

---

### Post by dryan775 on 2017-11-28
Gparted seems to have formatted the drive.
I now have one partition, 931mb
The Ubuntu installed let me install the system but when I went to reboot it without the LiveUSB, I got the Toshiba splash screen, then (quickly) this flashed by:  "error:  file '/boot/' not found."

If I reboot with the LiveUSB, it looks like the entire file structure is there.  OMG this is being ridiculous.

---

### Post by deadflowr on 2017-11-28
Now boot the live session and try to run boot repair/boot info to find out where things went awry:
Bot Repair: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Boot info: [https://help.ubuntu.com/community/Boot-Info]("https://help.ubuntu.com/community/Boot-Info")

---

### Post by dryan775 on 2017-11-28
OK, ran Boot-Repair
It says it fixed it, but when I reboot, I get

Failed to open \EFI\BOOT\grubx64.efi - Not Found

and crashes

---

### Post by oldfred on 2017-11-28
There should not even be /EFI/Boot/grubx64.efi, but have seen same error before.

It should be /EFI/ubuntu/grubx64.efi or /EFI/ubuntu/shimx64.efi or /EFI/Boot/bootx64.efi (which is a fallback entry that grub does not create, but Boot-Repair will copy shimx64.efi to bootx64.efi, but you may not have UEFI entry for it.

Post link to Summary Repair that Boot-Repair gives you. Do not post report as it is too long.

---

### Post by yetimon_64 on 2017-11-28
I'm getting a "Server not found" error on both of your (edit: pastebin) links. You may need to check the URL is correct and re-post a fixed link for anyone to see the boot-repair report.

---

### Post by deadflowr on 2017-11-28
Is the address for the boot repair output this:
[http://paste.ubuntu.com/26068108/]("http://paste.ubuntu.com/26068108/")
If so the posted output is off by a single / used instead of a dot.
paste/ubuntu is wrong
paste.ubuntu is right

---

### Post by oldfred on 2017-11-28
I suggest just running the full uninstall/reinstall of grub2 from Boot-Repair's advanced options.
Your UEFI entry is not the standard type.

What brand/model system? Some do require special settings.

---

### Post by dryan775 on 2017-11-29
Boot-Repair Postbin [http://paste/ubuntu.com/26068108/](http://paste/ubuntu.com/26068108/)

---

### Post by oldfred on 2017-11-29
See post #12. Your link is still wrong.

Did you run the suggestions in post #13?

---

### Post by dryan775 on 2017-11-30
#13 from oldfred worked!  I didn't know Boot-Repair had a Full uninstall and reinstall option, but it worked!

Thank you!

---

