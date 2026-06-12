---
title: "chnge monitor"
date: 2006-07-28
forum: General Help
---

### Post by Pathfinder_ on 2006-07-28
Hi, I know that when you change a monitor, in windows you have to install a driver for that monitor. the question is do I have to do anything in Ubuntu after I change it?

---

### Post by Anduu on 2006-07-28
Er...nope....

If your new monitor has resolutions/refresh rates that your old monitor doesn't you may have to tinker with your xorg.conf to be able to use them.

---

### Post by Pathfinder_ on 2006-07-28
the old crt supports all the resolutions and refresh rates of the new lcd. so does this mean i don't need to change anything?

---

### Post by jeremy on 2006-07-30
> **Pathfinder_ said:**
> the old crt supports all the resolutions and refresh rates of the new lcd. so does this mean i don't need to change anything?

In that case, no.

---

### Post by taurus on 2006-07-30
But if you run into problem with X when you use your new monitor, then run this command from a prompt (since it will drop you into a console) to configure X again...

```

sudo dpkg-reconfigure xserver-xorg

```

---

