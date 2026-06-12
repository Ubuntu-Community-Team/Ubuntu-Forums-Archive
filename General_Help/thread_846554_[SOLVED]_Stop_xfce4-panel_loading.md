---
title: "[SOLVED] Stop xfce4-panel loading"
date: 2008-07-01
forum: General Help
---

### Post by KenBW2 on 2008-07-01
I've replaced xfce4-panel with my preferred gnome-panel. As it is I have in Startup apps:
```

Description      | Command
Kill XFCE Panel  | killall xfce-panel
Open Gnome Panel | gnome-panel

```

But it seems a bit back to front to wait for it to load, then kill it off. How do I stop it loading in the first place?

---

### Post by sisco311 on 2008-07-01
If you want to make gnome-panel default for all users press Alt+F2 and enter:
```
gksudo mousepad /etc/xdg/xfce4-session/xfce4-session.rc
```to edit the xfce4-session.rc file.
replace 
> Client?_Command=xfce4-panel
with:
> Client?_Command=gnome-panelsave the file and exit.

---

### Post by KenBW2 on 2008-07-01
Thanks :)
A couple of other things I noticed:
```

Client0_Command=xfwm4
Client3_Command=xfdesktop

```
Can I replace that with gtk-window-decorator (which Compiz currently starts) and whatever the gnome desktop command is respectively?

And can I add anything into that file? Eg Compiz always will start at startup, and it's cut down my login time :)

---

### Post by sisco311 on 2008-07-01
You can replace xfwm4 with compiz.

The easy way to set up this things is to run all the applications 
you need in a clean session(gnome-panel, compiz, ...), close all other applications
then select the Save session option from the Quit dialog and log out. Next time
you log out make sure the Save session option is not selected.

---

### Post by KenBW2 on 2008-07-01
I've had bad experiences with saving of sessions before, like not being able to unsave and having loads of apps loading at startup. I'm probably missing something obvious but I'm scared to go near it again.

---

### Post by sisco311 on 2008-07-01
You can play with the xfce4-session.rc file but first create a backup.
```
sudo /etc/xdg/xfce4-session/xfce4-session.rc /etc/xdg/xfce4-session/xfce4-session.rc-backup
```
restore the original with
```
sudo /etc/xdg/xfce4-session/xfce4-session.rc-backup /etc/xdg/xfce4-session/xfce4-session.rc
```

---

### Post by KenBW2 on 2008-07-01
Thanks for your help.

Marked as Solved :)

---

