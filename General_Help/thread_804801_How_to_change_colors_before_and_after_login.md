---
title: "How to change colors before and after login"
date: 2008-05-23
forum: General Help
---

### Post by wrgb2 on 2008-05-23
Is there a way to change the color of the screen (or the image being shown) just before and just after logging in.  I have changed the splash screen using Startup Manager, and the login theme, too, but I still get an Ubuntu orange screen just before and after logging in.
Thanks,

---

### Post by lswest on 2008-05-23
when you go to the login window preferences under the "local tab" you see the list of the themes.  below that is a small line that says "background color" and a color-select box.  Choose the color you want. (see attached file)

**unless you have gutsy (Ubuntu 7.10)*.  If you do use Gutsy then do this:**

```
sudo gedit /etc/gdm/PreSession/Default
```

and search for the part that says:
```
# Default value
if [ &#8220;x$BACKCOLOR&#8221; = &#8220;x&#8221; ]; then
BACKCOLOR="#dab082"
fi
```

and change it to:
```
# Default value
if [ &#8220;x$BACKCOLOR&#8221; = &#8220;x&#8221; ]; then
BACKCOLOR=(new color in hex)
fi
```


* if you're unsure of what version you use, you can check with ```
lsb_release -a
``` in the terminal.

---

