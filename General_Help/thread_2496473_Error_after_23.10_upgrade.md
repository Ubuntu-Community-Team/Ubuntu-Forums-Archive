---
title: "Error after 23.10 upgrade"
date: 2024-03-29
forum: General Help
---

### Post by jamesbr0nd1211 on 2024-03-29
Hello, after searching the internet for countless hours, I am stuck, I cannot figure this out. After an upgrade 23.10 I got this message. 

rEFInd - Booting OS


Starting grubx64.efi
Using load options ''
error: no server is specified.
error: no suitable video mode found.

If I press esc early enough I can get into the correct boot partition. However, once I hit this screen, it's too late and I have to reboot. 

How the heck do I fix this? :/

---

### Post by Rubi1200 on 2024-03-30
Hi and welcome to the forums :-)

Is Ubuntu the only operating system on the machine?

Is there a particular reason you are using rEFInd and not GRUB?

Please post the output of this:
```
cat /boot/efi/EFI/refind/refind.conf

```

I have never used anything other than GRUB but there are users here with more knowledge of rEFInd and who can perhaps offer some insights.

Good luck!

---

### Post by jamesbr0nd1211 on 2024-03-30
No particular reason, just the default my host uses for the ubuntu installation. 

No config file was located at that location.

---

### Post by Rubi1200 on 2024-03-30
As I said, I am not familiar with this bootloader.

Hopefully, someone here can assist.

---

