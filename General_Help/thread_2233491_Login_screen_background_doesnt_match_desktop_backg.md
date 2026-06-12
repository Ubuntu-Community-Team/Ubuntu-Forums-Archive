---
title: "Login screen background doesnt match desktop background (Ubuntu 14.04 with Xfce DE)"
date: 2014-07-08
forum: General Help
---

### Post by pretty_whistle on 2014-07-08
It's my understanding that the login screen background is supposed to match the desktop background and should do so automatically.  Well it hasnt.  It's chosen another jpg image from the same folder.

How can that be fixed?


I have Ubuntu 14.04 with Xfce DE.

---

### Post by grumblebum2 on 2014-07-09
Hi pretty_whistle,
Don't use xfce but imagine nautilus is no longer drawing the desktop.

Check this dconf setting....
```
gsettings get org.gnome.desktop.background picture-uri
```

Is that the picture you see at the login screen?

---

### Post by vasa1 on 2014-07-09
> **grumblebum2 said:**
> Hi pretty_whistle,
Don't use xfce but imagine nautilus is no longer drawing the desktop.

Check this dconf setting....
```
gsettings get org.gnome.desktop.background picture-uri
```

Is that the picture you see at the login screen?
My suspicion is that Xfce may not observe some things. There, Thunar is in charge of the desktop. Anyway, OP may want to poke around a bit more in the gsettings business. I found this link very nice: [http://askubuntu.com/a/191013](http://askubuntu.com/a/191013)

---

### Post by pretty_whistle on 2014-07-09
> **grumblebum2 said:**
> Hi pretty_whistle,
Don't use xfce but imagine nautilus is no longer drawing the desktop.

Check this dconf setting....
```
gsettings get org.gnome.desktop.background picture-uri
```

Is that the picture you see at the login screen?

Nope.

---

### Post by pretty_whistle on 2014-07-09
I tried changing this dconf setting to no avail:

com>canonical>unity greeter>background


:(

I used the dconf editor for this.

---

### Post by grumblebum2 on 2014-07-09
I think it must rely on nautilus being the default file manager and drawing the desktop.
In my normal account nemo is my default file manager and draws the desktop. The greeter doesn't change when I change the desktop background.

In my test account where settings are default(nautilus is default file manager), if I change the desktop background
the unity greeter also changes.

---

