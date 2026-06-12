---
title: "Prog disappeared?"
date: 2007-05-23
forum: General Help
---

### Post by evilc on 2007-05-23
I had a glitch in beryl which I fixed but now I noticed I do not have add & remove or update manager in my list of programs? How can I get them back.

tia

---

### Post by Znupi on 2007-05-23
Right Click on **Applications** and click **Edit Menus**. Under **Items** (the right pane), the last item should be **Add/Remove**, and if it is, the checkbox right next to it is probably disabled. Enable it.

If **Add/Remove** doesn't appear at all, add it by clicking **New Item** and fill in with these:
-- **Type:** Application
-- **Name:** Add/Remove...
-- **Command:** gnome-app-install
-- **Comment:** Install and remove applications

You can choose an icon for it, too. The default is located at
```
/usr/share/icons/hicolor/scalable/apps/gnome-app-install.svg
```

---

### Post by evilc on 2007-05-23
Thanks for that, didn't know the "command", now all I got to do is find the update manager.:D

---

### Post by evilc on 2007-05-23
Oops just tried to run add/remove claims no such file or directory??

---

### Post by Znupi on 2007-05-24
> **evilc said:**
> Oops just tried to run add/remove claims no such file or directory??
If there is no gnome-app-install file under /usr/bin then something is really wrong. If you didn't delete that on purpose, it means someone else did it. Or **something** else... ;)

---

### Post by Znupi on 2007-05-24
> **evilc said:**
> Thanks for that, didn't know the "command", now all I got to do is find the update manager.:D
```

update-manager

```

---

### Post by evilc on 2007-05-24
> **Znupi said:**
> If there is no gnome-app-install file under /usr/bin then something is really wrong. If you didn't delete that on purpose, it means someone else did it. Or **something** else... ;)

Nope didn't delete it but had a glitch in beryl reinstalled that then noticed the 2 had gone?? Here is a locate for it:
/var/lib/dpkg/info/gnome-app-install.list
/var/lib/dpkg/info/gnome-app-install.postrm
/home/clive/.gconf/apps/gnome-app-install
/home/clive/.gconf/apps/gnome-app-install/%gconf.xml
/usr/share/locale-langpack/en_GB/LC_MESSAGES/gnome-app-install.mo
/usr/share/locale-langpack/en_AU/LC_MESSAGES/gnome-app-install.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/gnome-app-install.mo
/etc/gnome-app-install
/etc/gnome-app-install/packages-whitelist

Synaptic works and use that but would like it back again.

Just tried update-manager claims not installed have reinstalled now that one working, one to go.

---

### Post by Znupi on 2007-05-24
That's all the output that
```
/$ locate gnome-app-install
```
gave you?? In my case it's like a screen and a half of output (and I'm at 1280x1024). Try running
```

sudo apt-get check

```
See what happens.

---

### Post by evilc on 2007-05-24
OK, after re-installing update-manager I tried the same with gnome-app-install and it worked. It seems the problem was Python it claimed some files removed? No idea why/how but all back again, thanks for the help. :popcorn:

---

