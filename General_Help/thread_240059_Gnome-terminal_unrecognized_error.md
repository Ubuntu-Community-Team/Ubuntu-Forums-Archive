---
title: "Gnome-terminal unrecognized error"
date: 2006-08-20
forum: General Help
---

### Post by mucha on 2006-08-20
Hi, before the new updates to gnome-terminal it always worked fine. Now I get an unrecognized error like every third time I start it (and must restart every terminal). It's very annoying, is there anyone else that got the same problem?

---

### Post by rowanparker on 2006-08-20
What "unrecognized" error is this?

---

### Post by mucha on 2006-08-21
When I run gnome-terminal with an another terminal I get these errors:
```
** (gnome-terminal:7835): WARNING **: kan inte köra /usr/lib/libvte4/gnome-pty-helper
/home/simon/.themes/Rezlooks-Gilouche/gtk-2.0/gtkrc:186: error: invalid string constant "panel", expected valid string constant

```

In english it says that it cannot run /usr/lib/libvte4/gnome-pty-helper.
And thats not so strange because I don't even got the directory /usr/lib/libvte4/ after the libvte upgrade.

---

### Post by atie on 2006-08-22
@mucha, see [this]("http://www.compiz.net/viewtopic.php?pid=28028#p28028") and try the attached. Hope this helps you.

---

### Post by rowanparker on 2006-08-22
What is the attachment?
You should say what it is.

---

### Post by mucha on 2006-08-27
Unfortunately that didn't help at all, any other suggestions?

---

### Post by atie on 2006-08-28
If you're a compiz.net user, the gnome-terminal and vte packages were updated from there and even compiz.net removed them so compare your versions with below and reinstall the versions in Dapper(or Edgy) repo.

[https://launchpad.net/distros/ubuntu/+source/gnome-terminal](https://launchpad.net/distros/ubuntu/+source/gnome-terminal)
[https://launchpad.net/distros/ubuntu/+source/vte](https://launchpad.net/distros/ubuntu/+source/vte)

---

