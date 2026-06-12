---
title: "How to get text boot up like fedora instead of splash?"
date: 2007-12-11
forum: General Help
---

### Post by Vinno on 2007-12-11
Wondering if it possible to see the start console text and that of ubuntu instead of the splash screen?

Like in fedora startup screen it shows .eg
[PHP]

VSFTPD START                                                        [ OK ]
NTFS                                                                         [ OK ]
BLAHBLAH                                                               [ OK ]
BLAHBLAHBLAH                                                      [ OK ][/PHP]

---

### Post by scott_g on 2007-12-12
Don't know if there is any pretty way, like the method Fedora uses (with the terminal centered on the screen), but you could try the Alt-F2 combination to see the code that is executed.

Also (just thought this up; might not work...), you could try booting from the "recovery mode" (it shows the terminal commands), then add a command to the end of your /etc/rc.local file to start the x-server (startx or xstart, i can't remember which...).

Just an idea,
Scott

---

### Post by divague on 2007-12-12
i'm not sure if this will work, but you can do this install startupmanager and in the Boot Options tab, uncheck the show boot splash. Gutsy has startupmanager in its repos, i don't remember if early versions of ubuntu have it.

---

### Post by rsambuca on 2007-12-12
Yes, you can do it easily by removing the words 'quiet' and 'splash' from the end of the kernel line in your menu.lst.  If you need assistance with this, post the output of ```
cat /boot/grub/menu.lst
```and we can tell you exactly how to do it.

---

### Post by kpkeerthi on 2007-12-12
[Spice up your boot text]("http://ubuntuforums.org/showthread.php?t=50054")

---

### Post by Vinno on 2007-12-12
Used the removed quite splash from grub. Works nicely! thanks!

---

### Post by Hilipatti on 2007-12-12
runlevel 3 ? :P

---

