---
title: "Ubuntu 13.04, after update, window moving leaves trail"
date: 2013-10-13
forum: General Help
---

### Post by Pum on 2013-10-13
[[IMG]http://img203.imageshack.us/img203/9857/jse2.png[/IMG]](http://imageshack.us/photo/my-images/203/jse2.png/)

I made an update to day, when I moving windows it leaves trail like in image.
Tried different graphics drivers (313, 310, open source) from "Software & Updates" but without success.
In other desktops (Gnome) it looks OK with the same user.

BTW: if under moved window exists other window (not desktop) I see the trail but after 0.5 sec it removed.

Does some addition information needed for resolving the issue?


Thank you in advance.

---

### Post by varunendra on 2013-10-14
> **Pum said:**
> [[IMG]http://img203.imageshack.us/img203/9857/jse2.png[/IMG]](http://imageshack.us/photo/my-images/203/jse2.png/)

I made an update to day, when I moving windows it leaves trail like in image.
Tried different graphics drivers (313, 310, open source) from "Software & Updates" but without success.

Why have you posted this under virtualisation section of the forums? Is it a virtual machine you are talking about?
If so, you may need to install the latest drivers provided for 13.04 by the platform you are using (e.g. "Guest Additions" in virtualbox, or "VMware Tools" in vmware).

---

### Post by Pum on 2013-10-21
You right, my mistake, I created this post in wrong forum. My current ubuntu installation not under Virtual Machine.

---

### Post by varunendra on 2013-10-22
> **Pum said:**
> You right, my mistake, I created this post in wrong forum. My current ubuntu installation not under Virtual Machine.

Sorry, I'm not much experienced with graphics issues, but others maybe able to help with some more info. To help them help you, please open a terminal (Ctrl-Alt-T) and post back the outputs of (you may copy-paste these to avoid typo) -
```
uname -mr
lsb_release -d
cat /proc/cpuinfo | egrep 'model|cache' | sort -ru
free -m
lspci -nnk | grep -iA2 vga
sudo lshw -C display
```

You may also get relevant hints about graphics issues in /var/log/Xorg.0.log file.

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by QIII on 2013-10-22
*Moved to **General Help***

---

