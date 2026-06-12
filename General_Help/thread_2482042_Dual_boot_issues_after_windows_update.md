---
title: "Dual boot issues after windows update"
date: 2022-12-17
forum: General Help
---

### Post by elejele on 2022-12-17
Some windows update that forced itself on my dual boot configuration broke my grub loader, and now I can only boot up windows.
I have Ubuntu 20.04 running off a different hard drives than the windows (10 or 11) that came preloaded

On boot, the following message is displayed,
Failed to open \EFI\ubuntu\grubx64.efi - Not Found
Failed to load image \EFI\ubuntu\grub.efi - Not Found
start_image() returned Not Found, falling back to default

I ran the boot-repair diagnostic
[https://paste.ubuntu.com/p/97PZfPGvyk/](https://paste.ubuntu.com/p/97PZfPGvyk/)

I figured I seek help, because I don't really know what i'm doing!

Thanks!!

---

### Post by yancek on 2022-12-17
Beginning at line 17 of boot reparii, you see the contents of the EFI partition which has neither of the files indicated in the error message therefore, the error message.  If you scroll down to line 97 of boot repair you will see the Ubuntu entry in EFI which includes the shimx64.efi file.  That file also exists on the EFI partition so access the BIOS with the windows drive plugged in and select the Ubuntu option in the BIOS firmware (Boot0001) and boot and if successfull, run sudo update-grub.

---

### Post by elejele on 2022-12-17
Thanks, I think i see what you mean. In BIOS, the boot order menu lists Ubuntu as first in order. I have also tried to select the Ubuntu option from the temporary boot order menu as well but nothing happens (blank screen and i get returned to the boot menu).

---

### Post by tea for one on 2022-12-17
[COLOR="#0000FF"]Line 156[/COLOR] - nvme0n1p1	: hidenESP,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot

Can you boot into a live session, open Gparted or similar and check the flags on nvme0n1p1?
It appears to be hidden and, possibly, preventing Lubuntu from booting?

By the way, as you have Windows on one disk and Lubuntu on a separate disk, it would be more robust if each disk had an EFI System Partition.
If the ESP on one OS misbehaves, then you can boot the other OS via the PC UEFI boot menu.

---

### Post by elejele on 2022-12-17
I managed resolve it by reinstalling grub (ubuntu usb) by  [https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows(simply](https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows(simply)  updating didn't work)  taking into account the the separate EFI  partition. 


Thanks tea for one, didn't know about EFI partitions prior to this and will keep that in mind for the future!

BTW the boot-repair tool never worked for me and would hang on applying changes.

---

### Post by dragonfly41 on 2022-12-17
Also keep rEFInd in mind as  grub alternative .. I use it for dual (in fact multi) boot, with Windows in the internal SSD and Ubuntu(s) in external SSD(s) using a dual docking bay.

---

