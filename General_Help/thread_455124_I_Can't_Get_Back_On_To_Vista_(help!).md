---
title: "I Can't Get Back On To Vista (help!)"
date: 2007-05-26
forum: General Help
---

### Post by David_s on 2007-05-26
i've just installed Wubi and got Ubuntu running but now i want to go back to Vista because i need to access some things but i have no idea how to do it. 

I have searched the internet and i read that i am supposed to see an option when i reboot but i see none what-so-ever.

I don't knonw whether i should just delete all the Wubi files or what but if anyone can help me it will be greatly appriciated.

Thank you in advance.

---

### Post by meng on 2007-05-26
When you boot, do you see a message something like:
GRUB booting in ... 3 ... 2 ... 1... 0

If so, you need to press ESC while it is counting down and it should bring up the bootloader menu.

If you don't see it, just press ESC anyway several times from reboot and see if the menu comes up.

---

### Post by David_s on 2007-05-26
> **meng said:**
> When you boot, do you see a message something like:
GRUB booting in ... 3 ... 2 ... 1... 0

If so, you need to press ESC while it is counting down and it should bring up the bootloader menu.

If you don't see it, just press ESC anyway several times from reboot and see if the menu comes up.

Thank u very much i will try that now :) i hope it works.

---

### Post by David_s on 2007-05-26
It didn't seem to work so i guess i will have to try and install Vista again.

Thank you for the help anyway.

---

### Post by Computer Guru on 2007-05-26
You do not need to reinstall Vista.
Just boot from the DVD, and select "startup repair" - Vista will do the rest.

---

### Post by 2boo4you on 2007-05-27
if i install ubuntu (with wubi) can i the do it backwords (to get back into my XP)

---

### Post by revchris on 2007-05-31
> **Computer Guru said:**
> You do not need to reinstall Vista.
Just boot from the DVD, and select "startup repair" - Vista will do the rest.

I tried that but failed...Vista came back saying that there was no MBR or it was corrupt.

---

### Post by pawitp on 2007-05-31
See: [http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/faq.html](http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/faq.html)
Vista is not supported and it is highly likely that wubi broken Vista's MBR

---

### Post by MikeM709 on 2007-05-31
I tried that too with the startup repair and i was luckier. it said nothing was wrong though, which means it isn't broken, it just refuses to see it. is there any way that I can use a live boot cd of ubuntu and just follow the directions to manually uninstall the files? usually ubuntu didn't work for me and i was surprised when it did, so i'm thinking that it was the fiesty fawn that made it work. so if i use the live ubuntu cd, then i go into my hard drive, edit the stuff they mention here:[ https://wiki.ubuntu.com/WubiGuide#head-6b9eb58ace9884384e5e0d197bcf4159a25ed267]( https://wiki.ubuntu.com/WubiGuide#head-6b9eb58ace9884384e5e0d197bcf4159a25ed267) and hopefully get everything working back to normal.

---

