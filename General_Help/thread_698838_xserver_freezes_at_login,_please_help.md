---
title: "xserver freezes at login, please help"
date: 2008-02-16
forum: General Help
---

### Post by ziofil on 2008-02-16
hi everybody, today i'm sad..
i'm writing from another computer, because mine stopped working, in fact as the system gets to the login screen it *freezes*, and i can't even switch to ttys1 by pressing ctrl+alt+F1, because the keyboard is not responding...
i can run it in recovery mode, by selecting the entry in grub, but then as i try to run a startx command from root it freezes again...
i don't really know what to do, everything started when i got an apt-get error, so i had to run a dpkg --configure -a and it told me that /lib/modules/2.6.23.12 didn't exist, so i linked the /lib/modules/2.6.22.something to the directory that it was looking for... it seemed to work, but as i tried to reboot... bang...
please help me! :(

---

### Post by s3gfault on 2008-02-16
hmm, i would boot from a livecd and undo the changes you made that broke it.

---

### Post by ziofil on 2008-02-16
i'll try, but how do i undo that?
i already deleted the link in /lib/modules

---

### Post by ziofil on 2008-02-16
oh , great, it freezes during the startup process from the livecd!!
what does this mean?

---

### Post by ziofil on 2008-02-16
wow, i tried to boot it several times with the livecd and it was always freezing...
and then i tried again in recovery mode for a pair of times and it was freezing...
and then once in normal mode... and it worked!
i don't really have any idea what's going on... maybe a problem with hardware?
is my motherboard going to die..?

---

### Post by ziofil on 2008-02-16
nope... it is freezing again...
i'll start a different thread, because i think the problem is about hardware..

---

