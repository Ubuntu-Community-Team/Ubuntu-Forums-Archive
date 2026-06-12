---
title: "F-Spot not loading"
date: 2007-06-10
forum: General Help
---

### Post by Donnw on 2007-06-10
F-spot photo manager does not load up. A box appears on the task bar at the bottom of the screen telling me that F-spot is starting but disappears after about 20s, then nothing else happens.  I also have a similar problem with Webhttrack which was installed using Synaptic. Nothing at all happens when I try to load this from the icon in the menu.  F-spot used to work when I first installed  Ubuntu but just stopped working.  I have version 7.04 of Ubuntu installed

---

### Post by stijngysemans on 2007-06-12
Maybe what you can do is start f-spot using the command line.
Go to applications, accessories > terminal
type the following command
```

f-spot

```
Maybe you can get a lot more feedback then.

---

### Post by Donnw on 2007-06-12
i have just tried starting it from the terminal  and the following message appears which endlessly scrolls down the screen

Cant get a connection to the dbus. trying again ....Starting new Fspot server

---

### Post by stijngysemans on 2007-06-19
you still got this problem?
If you have,
maybe send your problem to the f-spot mailinglist! I'm prety sure they can help you in a better way then we can!
[http://mail.gnome.org/mailman/listinfo/f-spot-list](http://mail.gnome.org/mailman/listinfo/f-spot-list)

---

### Post by floke on 2007-06-19
Do other gnome apps work, or is it just fspot?

---

### Post by Donnw on 2007-06-21
Just F-spot does not load, other Gnome apps work ok

---

### Post by fabiomb on 2007-06-30
delete the folder .gnome2/f-spot and it will work, i don't know what is the problem, but when f-spot restarts the files, it works

---

### Post by Donnw on 2007-07-10
Thanks, very much, deleting the folder worked. F-Spot photo manager now works, however F-Spot photo viewer still doesn't  load up.

---

### Post by schpunty on 2007-07-22
At the risk of sounding totally stupid, I am having the same issue. Where do I or How do I delete this?
Help is greatly appreciated.
Thanks

---

### Post by Meurglys on 2007-08-11
> **schpunty said:**
> At the risk of sounding totally stupid, I am having the same issue. Where do I or How do I delete this?
Help is greatly appreciated.
Thanks

In your home directory. You will have to have "view hidden files" enabled.

Thanks for the solution, worked great for me. :)

---

