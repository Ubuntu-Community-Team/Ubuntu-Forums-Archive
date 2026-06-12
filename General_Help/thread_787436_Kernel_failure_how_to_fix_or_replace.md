---
title: "Kernel failure? how to fix or replace?"
date: 2008-05-08
forum: General Help
---

### Post by teryowen on 2008-05-08
My grub works fine and then it begins to load ubuntu where ubuntu tries to look for a boot image but cant find it so then it starts doing some other stuff where it begins to fail.

I think the kernel failed or something, so can i replace it. fix it or reinstall it.

By the way i'm using Hardy 8.04, i upgraded from gusty 7.10

---

### Post by macaholic on 2008-05-08
Could you possibly be more specific as to what it says? (I know it's hard to read and keep track of during boot, been there, doen that.) It would help diagnose your specific problem. If you want to completely get rid of the kernel and reinstall it, you could always purge it through apt-get (command will vary depending on what kernel you have), or "completely remove" it via synaptic.

---

### Post by teryowen on 2008-05-09
Here are the errors that I read off:

No resume image, doing normal boot

modprobe no such directory

setting kernel variable 
FAIL

mount error (around 5 of them)

Automatically will reboot in 5 seconds

ill try and read of more of them, but any ideas yet?

EDIT: is there any log file where i can check all the errors?

---

### Post by buntunub on 2008-05-09
You just need to fix your menu.lst to point to the right place where your kernel image is located.

---

### Post by teryowen on 2008-05-09
GRUB is fine i dont think the problem is with that, its not like i changed anything in the menu.lst file.

---

