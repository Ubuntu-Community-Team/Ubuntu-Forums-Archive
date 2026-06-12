---
title: "Help needed.  Ubuntu crash."
date: 2007-01-15
forum: General Help
---

### Post by jake3988 on 2007-01-15
I was trobleshooting my sound which suddenly stopped working.  I added the line: snd-emu10k1 to /etc/modules and rebooted.  For some reason /sbin/modprobe is failing and preventing ubuntu from starting up.

There's been no way I can think of to recover (to edit the darn file) and apparently its screwed up Mandrake too as I'm stuck in this bizarre half-X half-commandline thing.

Thanks!

---

### Post by jordilin on 2007-01-15
You can boot from a live cd, mount the filesystem and edit the file you changed. Hope that helps.

---

### Post by jake3988 on 2007-01-15
Thanks.  I knew I should have brought my cd from home.  Thank goodness I still have the .iso on my other partition, all I need to do is grab an empty cd somewhere to burn it.


By the way, any idea why loading mandrake from grub only loads this weird half-x half-command line thing?  (There's just a commandline box in the upper left of the screen)

---

### Post by jordilin on 2007-01-16
> **jake3988 said:**
> Thanks.  I knew I should have brought my cd from home.  Thank goodness I still have the .iso on my other partition, all I need to do is grab an empty cd somewhere to burn it.


By the way, any idea why loading mandrake from grub only loads this weird half-x half-command line thing?  (There's just a commandline box in the upper left of the screen)

I don't know, perhaps sth related to the X server. If so, I would consider reinstalling the OS, in  Linux is just a moment. :-D

---

### Post by jake3988 on 2007-01-16
Oh man, if only it were :(

---

### Post by Delkster on 2007-01-16
> **jake3988 said:**
> By the way, any idea why loading mandrake from grub only loads this weird half-x half-command line thing?  (There's just a commandline box in the upper left of the screen)

I know nothing about Mandrake but that sounds like a basic xterm-only failsafe X session. If you have a graphical login screen (i.e. gdm, kdm or something like that), have you tried explicitly selecting a KDE session from the menus in the login window?

---

### Post by jake3988 on 2007-01-17
Yeah.  But I figured out what the problem was.  For some reason gdm wasn't starting the selected graphical environment I chose, just X itself.

So, I type startkde on the command-line and viola... a graphical environment.  Granted, I hate kde and I'll change to icewm later, but I'm happy for now.

---

