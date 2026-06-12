---
title: "Ubuntu Doesn't Even Load"
date: 2007-08-08
forum: General Help
---

### Post by definedglory on 2007-08-08
So I'm running a dual boot with Windows XP and Ubuntu through Wubi and it has been working awesome until today. When I select Ubuntu from the OS Choice List it goes to the splash screen and then loads a little and then gives me this screen.

BusyBox v1.1.3 (Debian 1:1.1-3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

I have no idea what to do.

---

### Post by overdrank on 2007-08-09
> **definedglory said:**
> So I'm running a dual boot with Windows XP and Ubuntu through Wubi and it has been working awesome until today. When I select Ubuntu from the OS Choice List it goes to the splash screen and then loads a little and then gives me this screen.

BusyBox v1.1.3 (Debian 1:1.1-3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

I have no idea what to do.

HI I am not saying to start a new thread but if you are using wubi it might be of more help to place it in this forum for better support
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

---

### Post by n3hu on 2008-01-11
I had the same problem tonight with my Wubi install.
To fix it I ran "chkdsk /f" from windows xp. I actually
booted using "ultimate boot cd for windows" which may
or may not have been necessary. For a more detailed
check (it takes forever) you can run "chkdsk /r".

  the /f found several error is a *long* file which
I'm guessing was the ubuntu img file.

If that didn't work, plan-B was to restore the wubi
directory (in windows) from my backup/recovery
copy on a usb drive.

gl

---

