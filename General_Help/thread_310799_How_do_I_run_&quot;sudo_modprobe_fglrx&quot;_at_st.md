---
title: "How do I run &quot;sudo modprobe fglrx&quot; at startup?"
date: 2006-12-01
forum: General Help
---

### Post by escape on 2006-12-01
I want to run this before Xorg/Xgl starts; as it is now, Xgl won't load and fglrx gives me Mesa drivers until I do a sudo killall gdm and sudo modprob fglrx.

So, how do I run ```
sudo modprobe fglrx
``` before X, or basically have the fglrx module loaded at startup?

Note I haven't blacklisted it anywhere, it just doesn't seem to load on its own...

---

### Post by bettlebrox on 2006-12-01
add the module to /etc/modules

---

### Post by leonedo on 2006-12-01
sudo gedit /etc/rc.local

then put what ever you need in there

---

### Post by bettlebrox on 2006-12-02
> **leonedo said:**
> sudo gedit /etc/rc.local

then put what ever you need in there

rc.local is for scripts or commands you want to run at boot-time. /etc/modules is where you add modules you want loaded at boot-time. From the modules man page:

/etc/modules - kernel modules to load at boot time

Luck

---

### Post by escape on 2006-12-02
/etc/modules did it, right, thanks. I think I removed from there at one point when trying to build my own driver.

Man I'm an idiot...

---

### Post by bettlebrox on 2006-12-03
lol. these things happen!

---

