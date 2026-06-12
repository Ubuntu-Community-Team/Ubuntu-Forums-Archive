---
title: "help, I accedentally disabled my gui..."
date: 2006-10-11
forum: General Help
---

### Post by ShadowDust on 2006-10-11
well, I just got my ubuntu installed last night, and I decided to have a look at all the system options, turns out that the logon gui service is the gui for the entire thing.....

so anyways, using the command prompt how do i restart the gui service...

---

### Post by dphipps on 2006-10-11
Try this.
```
sudo gdm
```

---

### Post by aysiu on 2006-10-11
dphipps, does that really work?

I'd always thought you had to type ```
sudo /etc/init.d/gdm restart
```

---

### Post by ayoli on 2006-10-11
> **aysiu said:**
> dphipps, does that really work?

I'd always thought you had to type ```
sudo /etc/init.d/gdm restart
```

sudo gdm will work, but it's cleaner way to use /etc/init.d/gdm start|restart|stop

---

### Post by aysiu on 2006-10-11
What's the difference?

---

### Post by ayoli on 2006-10-11
hum not many diff i guess, more facility to restart (instead of killall gdm-binary, then sudo gdm). for other diff we have to look at gdm script in /etc/init.d

---

### Post by aysiu on 2006-10-11
Ah, good point--more options.

---

