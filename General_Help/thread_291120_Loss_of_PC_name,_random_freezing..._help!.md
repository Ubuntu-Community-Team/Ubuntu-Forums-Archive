---
title: "Loss of PC name, random freezing... help!"
date: 2006-11-02
forum: General Help
---

### Post by pattymnaish on 2006-11-02
I'm having a very weird situation with my computer. I'm reasonably sure it is not a hardware issue, so I won't list the PC specs here.
 After happily using Ubuntu for a few days, it suddenly lost its name. So, in a terminal, instead of: ```
patrick@desktop:~$
``` I get ```
patrick@:~$
```. On the login screen there is just a blank space instead of "Desktop".
 Secondly, half the time my computer freezes upon reaching the login screen, and I have to continually reboot.
 Please help ](*,)

---

### Post by pattymnaish on 2006-11-02
Also, sometimes it takes ages to start up (about 30 mins) and sometimes only about 20 seconds. :?

---

### Post by galileon on 2006-11-02
try to edit your grub configuration and get rid of splash and quiet

sudo gedit /boot/grub/menu.lst

look for your default bootup line, remove 'quiet' and 'splash'

this may give you hints at bootup about whats wrong

---

### Post by pattymnaish on 2006-11-02
I have previously done so, but the text goes by too fast for me to analyse it :?
Thanks anyway.

---

### Post by galileon on 2006-11-02
dmesg will tell u about kernel messages, but i dont know how to find about services... try looking through /var/log/syslog

---

### Post by pattymnaish on 2006-11-03
Thanks, I'll try.

---

### Post by pattymnaish on 2006-11-03
I've just got the name back :). I can live with the freezing.

---

