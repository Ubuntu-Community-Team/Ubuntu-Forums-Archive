---
title: "Ubuntu wont load from USB stick"
date: 2014-09-22
forum: General Help
---

### Post by snowmobiler on 2014-09-22
I have a Dell latitude D820 laptop that was running XP. I reformatted the HD to erase it first. Now I am trying to load Ubuntu from a USB stick since the laptop only has a CD drive. I used Ubuntu 14.04 running on one of my PCs and I used the ISO DVD I created as the source and an 8GB Sandisk Cruzer USB drive. I set the reserved extra space to 2GB. WHen I try to load I get the error that there is no Operating system and BOot Manager is missing. According to Ubuntu, the files and bootloader were copied successfully. So either it is the USB drive (which I formatted to Fat 32 first), or the Dell laptop is blocking this boot as it was a business laptop. Not sure what I would need to change here.

Edit-- I do have the option to boot from USB mass storage, but maybe the question is does it need to say USB-disk? And I forgot, the laptop only has a CD drive not a DVD drive. I tried an external DVD drive, but that did not work either

---

### Post by ian-weisser on 2014-09-22
Go back into your boot options and try all that include USB. One at a time.

To verify the USB stick, you can try it in any other machine.

---

### Post by snowmobiler on 2014-09-22
> **ian-weisser said:**
> Go back into your boot options and try all that include USB. One at a time.

To verify the USB stick, you can try it in any other machine.

Ok, I tried it on my compaq pc running win vista and when i chose the USB option to boot I got the same "operating system missing" error. I used the create boot disk option in Ubuntu 14.04 and the DVD I burned to load the software to begin with. I looked at the contents and the boot folder is there. Is there anything special you need to do to a USB stick to prepare it for boot creation? ALl I did was reformat the whole thing as Fat32. Do you need to create a boot partition or anything? Or is the sandisk cruser glide just not a good option?

---

### Post by yancek on 2014-09-22
What software did you use to put the DVD iso on the flash drive?  dd command, unetbootin, pendrivelinux, some other software?  Copying the files successfully to the flash will not make it bootable.  The suggestions above would be a good place to start.

---

### Post by snowmobiler on 2014-09-22
I used the program in Ubuntu, Startup Disk Creator.

---

### Post by snowmobiler on 2014-09-22
I also used EaseUS partition manager to format the stick as Fat32. The current type of drive it is now is GPT(data partition). I obviously wiped the previous attempt. Do I need to make the partition something else? I can't seem to do that, but does it have to be a MBR partition before I burn the ISO to it?

Instructions for creating USB boot disk is that it was recommended to erase the stick.

---

### Post by sammiev on 2014-09-22
Just format the USB as Fat32 and try  unetbootin to write the ISO.

---

### Post by sudodus on 2014-09-23
> **snowmobiler said:**
> I also used EaseUS partition manager to format the stick as Fat32. The current type of drive it is now is GPT(data partition). I obviously wiped the previous attempt. Do I need to make the partition something else? I can't seem to do that, but does it have to be a MBR partition before I burn the ISO to it?

Instructions for creating USB boot disk is that it was recommended to erase the stick.

I think the problem might be that the pendrive has a GPT partition table but lacks a 1 MB partition with the ***bios_grub*** flag. If that is the case you can either make such a partition, or make an old style MSDOS partition table with a partition with FAT32 and try again with the Ubuntu Startup Disk Creator. See details about making a working GPT system here
[URL="http://ubuntuforums.org/showthread.php?t=2213631"]
Portable installed system that boots in UEFI as well as in BIOS mode[/URL]

You can also try ***mkusb***, which will need no preparation of the pendrive (it will overwrite the boot sector, partition table and the drive as far as the content of the iso file reaches. See the description here

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by snowmobiler on 2014-09-23
I really think its due to the GPT partition. I was able to initialize the stick to MBR (like the other USB drives I have), then reformatted the stick to Fat 32. Trying to redo the ISO now.

**Edit**   Yep, that was it. Got the stick to boot to the install/try screen. Just don't have time to mess with the install this morning. Gotta go to work.:(

---

### Post by sudodus on 2014-09-23
Congratulations :KS

If you have no other boot-related problem, please mark this thread as SOLVED (click on **Thread Tools** at the top of this page).

If there is a different problem later on, it is better to start a new thread with a good descriptive title, in order to attract people who know about that problem.

---

