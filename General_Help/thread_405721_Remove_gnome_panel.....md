---
title: "Remove gnome panel...."
date: 2007-04-10
forum: General Help
---

### Post by jruo on 2007-04-10
Hi !

How do i remove the gnome panel with the appliction menu. And how do i prevent the user to rightclick on the desktop?
And i want to disable alt + f2.
The computer has a automatic login and opera starts in kioskmode, so i dont want any panels and no abillity to rightclick on the desktop.
I have disabled ctrl +alt + backspace and the virtual terminals, are there any more shortkeys i need to disable?
//jruo

---

### Post by swamytk on 2007-04-10
check with gconf-editor - as per my knowledge...

---

### Post by zvacet on 2007-04-10
Right click on the panel>delete this panel For second I don´t know.

---

### Post by josephus on 2007-04-10
Remove all the keybindings in System->Preferences->Keyboard Shortcuts

In gconf-editor under nautilus find the entry which says draw desktop and uncheck.  This will prevent the right click behaviour.

To remove gnome-panels altogether I think you have to go into alter the gnome-session to prevent it from starting up.

---

### Post by koshari on 2007-04-10
> are there any more shortkeys i need to disable?

how about cont-alt-f4 which changes the runlevel?

---

### Post by -sol0matrix- on 2007-11-17
to remove gnome panel completely just delete gnome-panel from your /usr/bin/ folder keep in mind that you might need it at an later time so make a copy of it

---

### Post by JohnnyD' on 2008-01-27
You can disable the gnome panel by going to Sessions-->Current Session and remove gnome panel from the list of running applications.

Then go to Session Options and click on the Remember button..

That's it..

Logout and the panel will not load up again

---

### Post by kimbaudi on 2008-04-06
-sol0matrix- said "to remove gnome panel completely just delete gnome-panel from your /usr/bin/ folder keep in mind that you might need it at an later time so make a copy of it"

Another solution to remove gnome panel completely using the terminal is to do the following:
1. Press ALT+F2 and type 'gnome-terminal' to access the terminal
2. type 'gnome-session-remove gnome-panel' and press ENTER

---

