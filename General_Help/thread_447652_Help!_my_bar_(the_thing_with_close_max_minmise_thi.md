---
title: "Help! my bar (the thing with close max minmise thing) has gone!"
date: 2007-05-18
forum: General Help
---

### Post by decilling on 2007-05-18
:( it just suddenly stoped showing up, its happening on every window i open. I did a restart and it still is doing it. i took a screenshot [IMG]http://img237.imageshack.us/img237/4859/screenshotvn4.png[/IMG]

that white block top left is the terminal. please get back to me asap

---

### Post by nereid on 2007-05-18
You need to restart metacity. Open the run window and type something like

```

metacity &

```

I'm not sure if metacity is the correct binary name, but the problem is, that your window manager had been killed  and your session was saved without it.

---

### Post by decilling on 2007-05-18
by run do you meen the terminal window? because I can't as the pic shows :(

---

### Post by ntetreau on 2007-05-18
Alt-F2 should open a window where you can type: 

metacity &

as mentionned by nereid

---

### Post by decilling on 2007-05-18
ok that did nothing :(

---

### Post by b0ng0 on 2007-05-18
Have you got Desktop Effects enabled? This usually causes the titlebars to disappear if you haven't changed your xorg.conf file.

---

### Post by Xbehave on 2007-05-18
if you cant find the command but you have beryl on your system then run beryl-manager and select reload window manager and reload window decorations

try running metacity in a console that may give you the reason metacity isn't working

if its that metacity's broken and not just you cant find the right command then you need to reconfigure xorg and metacity
i think the command is 
apt-get reconfigure metacity
apt-get reconfigure xorg
but as you only want to reconfigure the display of xorg there may  be a command to reconfigure just that

---

