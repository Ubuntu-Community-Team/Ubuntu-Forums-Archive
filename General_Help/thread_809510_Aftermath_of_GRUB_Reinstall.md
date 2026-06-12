---
title: "Aftermath of GRUB Reinstall"
date: 2008-05-27
forum: General Help
---

### Post by BlueToast on 2008-05-27
In continuation of [http://ubuntuforums.org/showthread.php?p=4995813](http://ubuntuforums.org/showthread.php?p=4995813):

So after reinstalling GRUB using the method I stated in my last reply to that thread, the GRUB loading screen with the Ubuntu logo finally shows up. Towards the very end of that loading bar, it brings me to one of the following sort of loading screens. Actually, I end up figuring out this is where it also stops or finishes loading, and that is also the next, new problem:
[img]http://www.hlrse.net/Qwerty/snapshot0001.gif[/img]

What? I thought I was supposed to see an Ubuntu login screen...

---

### Post by Gunman1982 on 2008-05-27
press ctrl+alt+F7 to see if you have a graphical server running (should show graphical login). If you see just black or little pixies running around or something then try ctrl+alt+F1 that should at least give you a text login.

---

### Post by lswest on 2008-05-28
that happened to me occasionally, and after i hit enter it loaded properly, and i checked my rc.local scripts, and found i had a startup script to run that no longer existed.  See if that's the case.

---

### Post by BlueToast on 2008-05-31
CTRL+ALT+F7 did nothing.
CTRL+ALT+F1 did nothing.
ENTER did nothing.
Booting into RECOVERY MODE (pressing ESC when GRUB is about to start) brang me to **root@Qwerty:~#** (console), and repeating the above did nothing.

EDIT :: The first two lines here worked now, after restarting it and trying again. CTRL+ALT+F7 cleared the screen. CTRL+ALT+F1 brang me to a text-based login screen, where I logged in and it brought me to **qwerty@Qwerty:~$**

> rc.local scriptsHow, where, and what?

EDIT :: /etc/rc.local -- but what am I supposed to look for? I'm a Windows user; I don't know anything about what is right or wrong in a place like this. *shrugs*


Result of 'startx'
[img]http://www.hlrse.net/Qwerty/snapshot0001.gif[/img]


Result of 'xorgconfig'
-bash: xorgconfig: command not found


Result of 'cat /etc/rc.local'
[img]http://www.hlrse.net/Qwerty/snapshot0002.gif[/img]

Result of 'xorg-config'
-bash: xorg-config: command not found


Result of 'xorgxconfig'
-bash: xorgxconfig: command not found


[color=red]**sudo dpkg-reconfigure xserver-xorg** apparently did the trick. _This thread is complete._[/color]

---

