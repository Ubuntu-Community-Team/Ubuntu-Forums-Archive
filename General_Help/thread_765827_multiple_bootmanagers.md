---
title: "multiple bootmanagers?"
date: 2008-04-24
forum: General Help
---

### Post by B@se on 2008-04-24
Lads,

currently I am downloading the latest release of ubuntu and want to use it with wubi. Besides using windows I am using another distro wich uses Grub for bootmanaging. (currently using solely for some great apps besides my ms stuff) 

So my question is currently, what exactly does wubi do, does it as I understand form the docu's and searching here, create a sub-account in the windows native bootmanager of does it overwrite grub?

The first option would be superb, currently not in the mood or have the time to clean up my Old installation, so it would suit me to just instal hh and start working with it.

Thanks in advance for your reply.

Kind regards from the Netherlands,

Bas

---

### Post by ago on 2008-04-25
[http://ubuntuforums.org/showthread.php?t=766039](http://ubuntuforums.org/showthread.php?t=766039)

---

### Post by B@se on 2008-04-25
Question answered here:
> **ago said:**
> Wubi will only modify the windows bootloader, it will not touch any other bootloader.

What it means is that you will still see the Grub Menu EXACTLY as it is, from there you will have to select Windows and from there you will be in NTLDR where you will be able to see Windows and Ubuntu. 

So when you already have grub the chain of events is:

Grub > NTLDR/BCD > GRUB4DOS > Kernel

Of course it would have been possible to modify the first grub menu directly, but supporting non-windows bootloaders when targeting squarely windows users is low on the priority list (if you have grub already chances are you do not really need Wubi to install Ubuntu...). It might be done in the next release.

[original post]("http://ubuntuforums.org/showthread.php?t=766039")

Thanks again.

Bas

---

### Post by B@se on 2008-04-25
hmm,

youre just to quick with replying... ;D

---

