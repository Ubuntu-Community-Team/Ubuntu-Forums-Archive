---
title: "Turn off pc speaker"
date: 2006-12-18
forum: General Help
---

### Post by ghepardo on 2006-12-18
How can I turn off the pc speaker?
Every time I close openoffice or I do some error in a terminal I hear the pc speaker. I want turn off that.
Is possible?

---

### Post by linuchsan on 2006-12-18
modprobe -r pcspkr
You can blacklist it, so it will not be loaded after a reboot.

---

### Post by ghepardo on 2006-12-18
> **linuchsan said:**
> modprobe -r pcspkr
You can blacklist it, so it will not be loaded after a reboot.

How to do that!? The blacklist thing.

---

### Post by po0f on 2006-12-18
ghepardo,

Add this to the end of /etc/modprobe.d/blacklist:
```
[FONT="Courier New"]blacklist pcspkr[/FONT]
```

---

### Post by ghepardo on 2006-12-18
> **po0f said:**
> ghepardo,

Add this to the end of /etc/modprobe.d/blacklist:
```
[FONT="Courier New"]blacklist pcspkr[/FONT]
```

Thank you.

---

### Post by hexion on 2006-12-18
Another option is to remove the module in /etc/rc.local adding this line before "exit 0":

> rmmod pcspkr

But, blacklisting is more elegant :D

---

### Post by po0f on 2006-12-18
hexion,

I think the preferred method of removing modules is `modprobe -r module`, but I forget the exact distinction that sets them apart.  (Or maybe I'm getting this confused with something else.)

---

