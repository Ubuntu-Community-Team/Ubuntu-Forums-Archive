---
title: "Failed to open \EFI\BOOT\grubx64.efi - Not Found (Dual Boot Ubuntu with Windows 11)"
date: 2023-03-13
forum: General Help
---

### Post by asimovjr on 2023-03-13
Same issue, worked for 2 days on my windows and now my ubuntu won't start.
I ran the boot repair, didn't work. I have attached the boot repair summary too.
Hope you would be able to help.
Thanks.

---

### Post by coffeecat on 2023-03-13
Moved to its own thread from here: [https://ubuntuforums.org/showthread.php?t=2474518](https://ubuntuforums.org/showthread.php?t=2474518)

---

### Post by asimovjr on 2023-03-13
I have a laptop that came installed with Windows 11. I installed Ubuntu 22.04, and it was running great for a while. Yesterday I booted into Windows, did nothing of note, and now the Ubuntu boot loader fails. The error message on boot is:


Failed to open \EFI\BOOT\grubx64.efi - Not Found
Failed to load image /EFI/ubuntu/grubx64.efi: Not Found
start_image() returned Not Found, falling back to default loader
Failed to open \EFI\BOOT\grubx64.efi - Not Found
Failed to load image /EFI/ubuntu/grubx64.efi: Not Found
start_image() returned Not Found


I ran boot-repair, and the report is in the attachment.
I am hoping that someone can take a look at this and tell me whether to make the recommend repairs, or to do something different.

---

### Post by coffeecat on 2023-03-13
Sorry - your earlier thread was accidentally locked. I've merged the two and made sure the merged thread is open.

Good luck and welcome to the forum.

---

### Post by yancek on 2023-03-13
If you looked atthe boot repair report, you will have seen there is no information on either windows or Ubuntu and in fact, nothing on the internal drive(s).  All the info is only for the USB you used.  Try running boot repair again and see if you get more output.  The UEFI info from the system board does show entries in UEFI mode for both windows and Ubuntu but boot repair shows 0 (zero) OS detected.

---

### Post by asimovjr on 2023-03-13
I am getting the same report again and again. After taking another look, I can't see any partitions as well from my Ubuntu. Is there anything else I can try?

---

### Post by yancek on 2023-03-14
You could try removing the drive from the current computer and attaching it to another working computer to see if it is recognized.  You may not have a dead drive but poor connections or connections gone bad.  Or check the connections on the drive on the current computer to make sure they are secure.

---

### Post by tea for one on 2023-03-14
Good suggestion from yancek in post 7.

Also, as you last used the PC in a Windows session, have you tried booting a Windows 11 iso and investigating Windows repair options?

---

### Post by asimovjr on 2023-03-14
I used "try ubuntu" to save my data, drives were visible there and healthy and then formatted that partition. I will install again, but first I need to remove old boot entry from BIOS. I have tried doing so from BIOS itself, try ubuntu's [COLOR=#232629][FONT=ui-monospace]efibootmgr -b 1 -B[/FONT][/COLOR] and Windows bcdedit, all of them were successful but the boot entry is still there in the BIOS. Is there any way I can be assured that my old ubuntu has been removed properly and completely?

---

