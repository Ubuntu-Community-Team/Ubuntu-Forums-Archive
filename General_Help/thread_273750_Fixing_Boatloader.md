---
title: "Fixing Boatloader"
date: 2006-10-08
forum: General Help
---

### Post by Happydude123 on 2006-10-08
I have a problem when I try to install ubuntu when I start up my computer after the livecd stuff my usb mouse doesn't work or my internet...and It says when it starts loading stuff that my modules.dep is missing.

Well I asked my friend who is very good with linux, he says that because I installed Mandriva 2007 and I didn't delete the LILO bootloader, it is having confliction with the ubuntu GRUB loader. Becuase of different startup and module loading I guess.

Well at startup, I still do see the mandriva boatloader and little screen.

How would I remove LILO and get the ubuntu loader?
Which is better lilo or grub?
Would a seperate boot partition forever fix my problem?

---

### Post by kidders on 2006-10-09
Hi there,

Ubuntu will happily cooperate with lilo, if that's what you're used to using. It seems as though you have more than one hard drive in your computer ... unless you've done something a bit strange, that's the only way you could wind up with two bootloaders. Typically, they're stored in the MBR, so creating a /boot partition won't have any effect.

> How would I remove LILO and get the ubuntu loader?
The handiest way is simply to overwrite it by installing grub on top of it.

> Which is better lilo or grub?
Imho grub is "better", but lilo is simpler :-) Lilo is very easy to use, but grub is much more helpful when something goes wrong.

> Would a seperate boot partition forever fix my problem?
No.

---

