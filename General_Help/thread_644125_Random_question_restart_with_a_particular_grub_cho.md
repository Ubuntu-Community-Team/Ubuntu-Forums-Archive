---
title: "Random question: restart with a particular grub choice in one command?"
date: 2007-12-18
forum: General Help
---

### Post by djbon2112 on 2007-12-18
Just as the title asks. Is there a command that would restart the computer and auto-select a particular choice in Grub (for instance, my Windows XP gaming install) for me?

It seems a little pointless I know, but it would be convenient to just open as shortcut, walk away for 2 minutes and be in Windows, then reboot when done and go in to Linux as normal. That, and the fact I don't want/need Grub to appear normally (Ubuntu is my main OS and I want the Windows install only for gaming when I need it).

---

### Post by ddrichardson on 2007-12-18
I dare say someone has a more elegant solution, but a script that puts a menu.lst where XP is the default before executing shutdown -r now would achieve this. Of course you would need another to reboot in Ubuntu by default.

---

### Post by r-mo on 2007-12-18
> **ddrichardson said:**
> I dare say someone has a more elegant solution, but a script that puts a menu.lst where XP is the default before executing shutdown -r now would achieve this. Of course you would need another to reboot in Ubuntu by default.

That was my thought too, Could you also write a script to run on windows startup to change the default back again?  I assume you could with the ext2 driver for xp, although I can't say I've ever installed it as I don't want to let windows touch my linux partitions.

---

### Post by djbon2112 on 2007-12-18
I'd be willing to try that (it's XP Embedded so it's completely stripped down), but I have no idea how to write such a script. Any pointers? Oh, and is there an x64 version of the ex3 driver? It's actually XP x64 edition stripped down! ;)

---

### Post by djbon2112 on 2007-12-18
Wow I'm completely lost on this. I tried creating a launcher to restart the machine, but of course it doesn't work. Anyone have any tips?

---

### Post by Schalken on 2007-12-18
KDE's shudown dialogue can have the "restart" button as a dropdown menu where you select the OS (from the entries in your /boot/grub/menu.lst) you would like it to reboot into. However, I don't know if it is enabled by default in Kubuntu, or how to enable it if it isn't.

I do recall GNOME's shutdown dialogue as having similar functionality, but I can't find it in Ubuntu. :S

---

### Post by djbon2112 on 2007-12-18
Hrm I'm really just looking for a simple shell command that'll work.

Simply putting:

```
sudo shutdown -r now
```

... into a launcher didn't start, and while I can see why, I have no idea how to make it do this.

Unless I can put it in a shell script to also do what ddrichardson suggested, but I've got no idea where to even start with that!

---

### Post by NeoIce on 2008-04-20
I hate to be a thread necromancer, but I was googling and this seemed CLOSE to my problem.

I'm creating a multi-OS desktop box just so I can try out every flavor of *NIX. (and general desktop use really just needs a GUI and a web browser, so why not?)  I'd like to configure GRUB (or some shell scripts I  guess) so that the OS selection is random, just for a fun challenge.  I'm guessing some sort of on-shutdown init script that edits the GRUB menu.lst would do it, but that means I'd have to have a GRUB_edit script configured in every flavor, correct?  certainly fits into that "fun challenge" aspect, but I like cleaner solutions if at all possible.

anyone have thoughts?  would anyone even be interested in something like this or am I just utterly crazy?

thanks :P

-rb

---

