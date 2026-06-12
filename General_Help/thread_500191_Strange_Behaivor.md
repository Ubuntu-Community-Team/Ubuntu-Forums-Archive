---
title: "Strange Behaivor"
date: 2007-07-13
forum: General Help
---

### Post by derrekito on 2007-07-13
I decided to install feisty on an older computer, and it has been acting strange ever since.

1)  the screen sometimes turns black when u log off or wont come out of screen savor mode.

2)  sometimes when you boot it, screen stays black, no boot screen, and the LED KEYBOARD indicator for caps lock and scroll lock just blink.  rebooting does nothing.  but waiting for a period of time or whatever and the pc decides to work.  (none of these issues existed until I installed ubuntu on it).

---

### Post by derrekito on 2007-07-14
Update:  It isn't random anymore, I cannot get the OS to boot.

---

### Post by derrekito on 2007-07-24
The OS boots now.  But now the PC wil not shut down on it's own, it sorta hangs on the shutdown process (Ubuntu logo screen) and we have to shut it off ourselves.  Any ideas wtf?

---

### Post by kvonb on 2007-07-24
How old is the computer?

What CPU does it have?

How much RAM?

What make/model of video card is in it?

Does the standard Ubuntu CD boot to the desktop ok, and work properly?

---

### Post by derrekito on 2007-07-24
> **kvonb said:**
> How old is the computer?

What CPU does it have?

How much RAM?

What make/model of video card is in it?

Does the standard Ubuntu CD boot to the desktop ok, and work properly?

CPU is an Old AMD 1.2 Ghz (single core, just a few months or so after CPU broke the 1 GHZ mark).  It's one of those older HP models (has that damned shitty modem/sound card whihc BTW has no drivers :( ) from back in the day.  Video card is a GeForce 2 with I believe 64 megs of on board ram.  The rest of the system has 256 MB of RAM.  The CD boots correctly.

---

### Post by Crafty Kisses on 2007-07-24
> **derrekito said:**
> The OS boots now.  But now the PC wil not shut down on it's own, it sorta hangs on the shutdown process (Ubuntu logo screen) and we have to shut it off ourselves.  Any ideas wtf?

You might want to try booting into verbose mode, and see where the error actually occurs, and then if that fails, I'm not sure if this will solve the problem but you can try reconfigure the X server, and that might solve the issue.

---

### Post by lisati on 2007-07-24
> **derrekito said:**
> The OS boots now.  But now the PC wil not shut down on it's own, it sorta hangs on the shutdown process (Ubuntu logo screen) and we have to shut it off ourselves.  Any ideas wtf?
I get some of the same symptoms as you have been experiencing on an old machine I have Win98SE on....I think my machine is just getting tired.

---

### Post by kvonb on 2007-07-24
You might want to try switching from the generic kernel to the 386 kernel.

I'm not sure it will fix it, but it can't hurt :).

If you can get it to boot, open a terminal, or drop to a VT (virtual terminal, press ctrl-alt-f1, then login with your regular username/password), and type this:

```
 sudo aptitude install linux-386
```

It will ask you for your password again, (use your normal login password) and if the net is working as it should, it will offer lots of packages to install, say yes.

When finished reboot (you can type: sudo reboot) and at the first boot screen (you might have to press escape) select the 386 kernel.

Hopefully that will work :).

---

