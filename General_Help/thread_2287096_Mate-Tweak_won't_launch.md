---
title: "Mate-Tweak won't launch"
date: 2015-07-16
forum: General Help
---

### Post by Nostigex on 2015-07-16
Here's the error message when attempting to launch it from the command line:

```
Traceback (most recent call last):
  File "/usr/bin/mate-tweak", line 31, in <module>
    from gi.repository import Gdk, GdkPixbuf, Gio, GObject, Gtk, Notify
ImportError: cannot import name Notify


```

Note: My "indicator applet complete" just crashed, which makes me wonder if there's a connection since it's a notification applet and the missing component above is named "Notify".

---

### Post by v3.xx on 2015-07-17
I have not experience this.

What version are you running?  I find 14.04 (long term support) to be very stable.

---

### Post by Nostigex on 2015-07-17
Fixed it. I uninstalled a bunch of stuff yesterday I didn't want and thought I didn't need, but apparently I removed components needed by mate-tweak and the indicator applets. I went to my Ubuntu Software Center history and reinstalled the packages in my removal history. I didn't see any way of marking packages for reinstallation as in Synaptic, so I had to type everything out in terminal. Mate-tweak started working again after reinstalling Mono and every package starting with 'gir' (one of them was named 'gir1.2-**notify**-0.7'). The applet worked again after a reboot.

---

### Post by v3.xx on 2015-07-17
Sounds good

The command
```
sudo apt-get -f install
```
can also be used to fix broken packages.
[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by vasa1 on 2015-07-17
> **Nostigex said:**
> ... Mate-tweak started working again after reinstalling **Mono** and every package starting with 'gir' ...
That's interesting. I wonder why Mono is necessary.

---

### Post by v3.xx on 2015-07-17
> **vasa1 said:**
> That's interesting. I wonder why Mono is necessary.
Its not necessary, its a optional install.

---

