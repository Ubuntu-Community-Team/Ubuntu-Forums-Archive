---
title: "Broke my xorg.conf with envy..."
date: 2007-06-15
forum: General Help
---

### Post by sondratheloser on 2007-06-15
I thought I would see if Envy would make videos stop skipping when I played them, but apparently, it broke my xserver instead.

Here is what I have tried to do to fix it:
I logged in (it just doesn't start up gnome), put in my password, and went to the X11 directory.  There I removed xorg.conf and replaced it with a backup from last night (when I ran envy).  Then i rebooted.  And, it didn't fix.  (I was silly and did not make my own backup -- I think envy made the one that was there, and there are two more backups in the X11 dir without dates, but I'm afraid to use those because then I will have to set up my wireless card alllllll over again)

So: here is my first question:  how can get the output of xorg.conf without using gnome so I can post it here/look at it.

I am booted into Vista right now, and it's driving me nuts.

Thanks, Sondra

---

### Post by jasonlfunk on 2007-06-15
when you start Ubuntu it should error when trying to start Xorg and then put you into a terminal. I belive if you then look in /var/log/syslog you should see your Xorg output.

---

### Post by Frozen001 on 2007-06-15
> **sondratheloser said:**
> two more backups in the X11 dir without dates, but I'm afraid to use those because then I will have to set up my wireless card alllllll over again)
Someone correct me if I am wrong, because I am stil a new user, but the xorg.conf has nothing to do with the wireless card...

---

### Post by BlahMan_of.Doom on 2007-06-15
> **Frozen001 said:**
> Someone correct me if I am wrong, because I am stil a new user, but the xorg.conf has nothing to do with the wireless card...

That's what I was thinking too ;)

---

