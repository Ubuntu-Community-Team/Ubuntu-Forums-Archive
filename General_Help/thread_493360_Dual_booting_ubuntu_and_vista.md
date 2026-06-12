---
title: "Dual booting ubuntu and vista"
date: 2007-07-05
forum: General Help
---

### Post by Akira459 on 2007-07-05
I am currently dual booting ubntu and XP and i am getting Vista in mail soon. I was just wondering how i upgrade XP to vista and keep ubuntu unaltered and able to dual boot with Vista.

If anyone could help shed some light on this i would appreciate it alot, thanks.

---

### Post by AriciU on 2007-07-05
Are you using the XP boot manager or GRUB as default?

When you will install Vista it will write it's boot manager on the MBR and kill Grub. You will have to get SuperGrubDisc, boot that and re-write Grub to the MBR replacing Vista's boot manager. Then you will have to add Vista's Bootloader to the /boot/grub/menu.lst in order to boot Vista..

I'll guide you thru it after you install Vista and are grub-less...

I don't know how to load Ubuntu to Vista's bootloader but maybe someone else could help you with that if you decide to do it that way.

---

### Post by Akira459 on 2007-07-05
yeah i go through grub then it brings me to me windows boot loader. what is a SuperGrubDisc? and will i have to reinstall ubuntu?

---

### Post by AriciU on 2007-07-05
No, you won't have to reinstall ubuntu.

I've just remembered that super grub disc is not needed. GRUB can be reinstalled from the Ubuntu LiveCD.

---

### Post by Akira459 on 2007-07-05
alright thats cool. since vista doesnt come til friday ill be posting either friday night or saturday askin for help so yeah.

---

