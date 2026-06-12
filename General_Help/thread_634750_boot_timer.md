---
title: "boot timer"
date: 2007-12-08
forum: General Help
---

### Post by sgt_spike on 2007-12-08
I have WinXP and Ubuntu and when my machine boots up Ubuntu put a boot timer on the boot sequence.  When the timer ends it boots to Ubuntu.  I want to stop this timer.  Any answers?

---

### Post by Herman on 2007-12-08
Hello sgt_spike,
You wouldn't be the spike I know would you? Probably not, never mind. :)

I like the timer to be disabled myself. 
If you want the GRUB menu to stay there and wait for you and not do anything until you make the decision, you just need to 'hash' or 'comment out' the line with the command for the timer in your /boot/grub/menu.lst file.

Use the following command to access your /boot/grub/menu.lst file, (you can copy it from this web page and paste it inot your terminal to save typing if you like,```
sudo gedit /boot/grub/menu.lst
```Here is what you want to do in the /boot/grub/menu.lst file, explained and illustrated, [Setting the timer]("http://users.bigpond.net.au/hermanzone/p15.htm#timer")

Regards, Herman :)

---

