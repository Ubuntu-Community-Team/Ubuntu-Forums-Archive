---
title: "Forgot Password. GRUB reset not working. Would like to wipe entire HD. Help needed!"
date: 2016-02-26
forum: General Help
---

### Post by username123452 on 2016-02-26
I went to Europe for 3 months and left my laptop at home and in the meantime I forgot my password. I tried doing the password reset through the GRUB menu thing (using 
```
mount -o rw,remount 
```
 and all that) and it didn't work, even after 5+ tries. Maybe it's important to note that I have a sda5_crypt setup on the computer which unlocks my disk if I enter a passphrase (which I remember - I just forgot my second password)... 

The data on my laptop isn't terribly important - I just need this computer to use for uni in a few days. I want to know if I can completely wipe it clean so it doesn't ask me for passwords anymore and so I can either start with a clean boot of Ubuntu or through a USB boot of Windows (either 8 or 10). How do I just completely wipe the computer? I've gotten into BIOS and GRUB and tried to boot up Windows 10 but it just doesn't recognize it (and I think I read somewhere that being able to boot any OS through BIOS/GRUB, etc. is a security flaw?). Anyway. I just need help. Sorry if I haven't provided enough info, ask and I shall try to answer.

Thank you so much for trying to help me if you can.

---

### Post by ian-weisser on 2016-02-26
The sole purpose on encrypting your data is to prevent everyone (who doesn't know the passphrase) from ever reading it, no matter what.
Your data is gone forever, unless you remember your passphrase. No workaround, no reset, no backdoor.

The passphrase isn't an account password, it's an encryption key.
The password reset method intended for unencrypted systems won't work. If it did work, that would be a rather huge security hole.

Reinstall Ubuntu however you installed it before.
Get out your install USB stick and boot from that.
If you wish to keep Windows, install Ubuntu carefully and remember how you preserved Windows last time. The Ubuntu installer will happily overwrite Windows 10 if you let it.
Reconsider the bother of encrypting a system that lacks much personal data or theft value.

---

