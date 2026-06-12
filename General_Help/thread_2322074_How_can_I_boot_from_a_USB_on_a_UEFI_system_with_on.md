---
title: "How can I boot from a USB on a UEFI system with only Ubuntu installed?"
date: 2016-04-26
forum: General Help
---

### Post by Saul_F._Borel on 2016-04-26
Hi,

I recently installed Ubuntu 16.04 on an Acer Aspire E1-572G laptop which came with Windows 10 preinstalled. 
What I did was create the Live USB and then from windows I chose an option that said something along the lines of "Reboot from EFI USB drive". Then I removed Windows 10 and installed Ubuntu.

Now, I have no way to access the BIOS or any sort of boot options on startup. When I turn on the computer, a screen with the word "Acer" flashes for half a second, then it goes straight to ubuntu.

So I was wondering, what happens if I want to install a different flavour of Linux or if I want to reinstall Windows from the recovery CD? Is there an option in Ubuntu to reboot from a USB drive or CD?

---

### Post by Bucky Ball on 2016-04-26
*Thread moved to **General Help**.*

Welcome. Seems your issue is you can't access your BIOS. You gotta be quick! At least I do. I start pressing immediately at the manufacturer splash screen, or even before!

On that split second screen it should show you the key to press to get to BIOS, if you don't already know it. Could be del, F2, ESC. Try them, check the manual.

Any luck? UEFI makes no difference here, goes to BIOS or Boot Device menu when I hit the correct key at boot.

PS: Win10 would have been in UEFI so you have tried the same procedure you did last time I suppose?

---

### Post by Saul_F._Borel on 2016-04-26
Hello!

I wasn't being quick enough. Turns out pressing Esc at just the right fraction of a second takes me to a GRUB screen. 
Still don't know how to boot from the USB, however. Can the GRUB screen help me?

Thanks!

---

### Post by Bucky Ball on 2016-04-26
Wrong key then. You should be getting to BIOS. Try the others I listed or, as I say, check the manual.

Actually, go F12. That gives the boot device menu on a lot of machines and would allow you to boot a USB in UEFI or legacy probably. Again, if F12 is not the key, check manual. 

Main thing is, you can get somewhere if you hit some key at the right time so no issue there. Just a matter of finding out which key takes you to the BIOS and which one takes you to the boot device menu. :-k

---

### Post by Saul_F._Borel on 2016-04-26
That was it. Thanks!

---

### Post by Bucky Ball on 2016-04-26
All good. Just to confirm: F12 got you to the boot device menu?

---

### Post by Saul_F._Borel on 2016-04-26
Yes, that was it

---

