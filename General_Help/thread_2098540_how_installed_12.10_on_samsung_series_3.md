---
title: "how installed 12.10 on samsung series 3"
date: 2012-12-26
forum: General Help
---

### Post by DD4lifeusmc on 2012-12-26
old computer crashed , forced buy new.
Samsung series 3 with win 8 installed   I hate windows.
Computer so new not on the website yet
UEFI - SECURE BOOT &FAST BOOT 
12.10 claims to support the above.  It does kind of. Here's what I had to do.
download the 12.10  64 bit ISO. I used unetbootin to create a live USB flash drive.
on my Samsung, turn off, turn on and hit F2 several times to get into the bios.
Go to boot section, click the bottom option on booting order.
Move the USB CD to top, Move the other USB options up under that.
Save and exit.
Reboot. The live USB should boot.
Now try 12.10 and see if it appears to work. If so select install. Now I got rid of windows on mine.
Let it use the whole disk.  When done unmount the system drive.
select Gparted, shrink the system partition down to 69 to 100 gig or your preference.
create a new partition with the new space. Label it etc.
When done eject the USB drive. Reboot.
Now mine faile to boot  Image was not accessable.  click escape. A menu popped up
5 or 6 options to boot from. None worked.
Shut down rebooted into the bios by hitting F2.
Went to security, disabled the UEFI secure boot.  Allowed system to boot and was up and running.
Do NOT enable fast boot. You will NOT ever get into the bios again.
So far Ubuntu is working.
They need to do more work on the secure certificate from Microsoft, so every computer can use the secure boot.
Now a different problem with truecrypt but that is another thread.
Good luck guys Microsoft and windows has screwed us again.

---

