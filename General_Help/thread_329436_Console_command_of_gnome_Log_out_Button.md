---
title: "Console command of gnome Log out Button"
date: 2007-01-01
forum: General Help
---

### Post by dfm21 on 2007-01-01
Hi!

What is the name of the command that's invoked by clicking the log out button in gnome panel? I googled for this for half an hour - unsuccessfully. :(
If I go to System -> Preferences -> Keyboard Shortcuts, there is an entry called "Log out", but it does not do anything when bound...

Thanks!

---

### Post by bapoumba on 2007-01-01
Hi,
I'm not sure I really understand what you are trying to do.
To exit the current gnome session : **gnome-session-save --kill** you'll get to the logout screen. If **gnome-session-save --kill --silent**, no questions asked, you'll get back to GDM. I do not know whether you can bind that to a keyboard shortcut.

---

### Post by dfm21 on 2007-01-02
Thanks, bapoumba!

The **gnome-session-save --kill** command was exactly what I was looking for. Binding it is kid's play with [xbindkeys]("http://hocwp.free.fr/xbindkeys/xbindkeys.html").
**gnome-session-save --kill --silent** could be coming handy too ;).

Greets!

---

### Post by bapoumba on 2007-01-02
Nice.
Greetings too ;)

---

### Post by conorsulli on 2008-04-19
Thanks for [COLOR="Green"]gnome-session-save --kill[/COLOR]
I had tried many commands like gnome-power-manager --logout and loads others. Now I can add this to my AWN taskbar. Very handy!:popcorn:

---

