---
title: "will wubi hurt grub?"
date: 2008-04-24
forum: General Help
---

### Post by alexandermimix on 2008-04-24
Currently I have ubuntu and xp installed with grub as my boot manager, I want to give wubi a whirl mainly for the amusement value of it. My question is:

Does wubi kill grub or will I merely be able to choose between wubi and XP AFTER having chosen XP from my grub menu? 
I just don't want to reboot and find that I have a choice of ONLY wubi or XP and end up having to reinstall / configure GRUB.


Thank you in advance to the clever soul who replies :)

---

### Post by get2gether on 2008-04-25
Im wondering the same thing, i have already pclinuxos installed with Xp on another partition. So my question is, will pclinuxos show up as well in the boot options using wubi?

---

### Post by B@se on 2008-04-25
yep,

had the exact same question [here]("http://ubuntuforums.org/showthread.php?t=765827")

I am wondering what the experts say.

Bas

---

### Post by ago on 2008-04-25
Wubi will only modify the windows bootloader, it will not touch any other bootloader.

What it means is that you will still see the Grub Menu EXACTLY as it is, from there you will have to select Windows and from there you will be in NTLDR where you will be able to see Windows and Ubuntu. 

So when you already have grub the chain of events is:

Grub > NTLDR/BCD > GRUB4DOS > Kernel

Of course it would have been possible to modify the first grub menu directly, but supporting non-windows bootloaders when targeting squarely windows users is low on the priority list (if you have grub already chances are you do not really need Wubi to install Ubuntu...). It might be done in the next release.

---

### Post by B@se on 2008-04-25
Hi Ago,

thanks for your reply,

quoted it in my orriginal post.

Going to grind some beens (and put on a brew) so I can get started installing.

Tnx.

Bas

---

### Post by alexandermimix on 2008-04-25
Thank you heaps for your reply. Something about this topic in the wubi wiki would be +1

:)

alexander

---

### Post by ago on 2008-04-25
> **alexandermimix said:**
> Thank you heaps for your reply. Something about this topic in the wubi wiki would be +1

hehe well said... "WIKI"... It means anybody can add to it... ;)

---

### Post by get2gether on 2008-04-28
Thanks for your time ago, i understand what you say here, though for me it is one possible way to get around having another os installed when i already have four partitions set up (grub only allows four)
Cheers!

---

### Post by ago on 2008-04-28
Grub supports whay more than 4 partitions, provided they are not all primary partitions (you need at least one extended partition). But Wubi does not require any partition per se'. The above is only for people that already have Grub AND Windows. All it happens is that if you install Wubi in such case, you have to select "Windows" first and then "Ubuntu".

---

