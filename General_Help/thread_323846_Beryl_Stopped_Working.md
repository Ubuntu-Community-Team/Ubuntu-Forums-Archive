---
title: "Beryl Stopped Working?"
date: 2006-12-22
forum: General Help
---

### Post by BetaMaster on 2006-12-22
I've been using Beryl for the past several days. Yesterday, it stopped working.
What happens now, is that Ubuntu starts up, and the taskbars on top and bottom don't show any icons or buttons or anything. The desktop is empty, and it's a plain brown image, rather than the wallpaper I use. Then the taskbars disappear, leaving just my mouse and the background. I can't right click or anything, but I can move the mouse. Nothing else happens.

If I revert to the backed-up xorg.conf and gdm.conf-custom files, and remove everything about Beryl, through the command line, I can use Ubuntu fine again.

But then when I install Beryl again, the same thing happens.

It was working fine before - can anyone help me?

Thank you!

---

### Post by cacharreo on 2006-12-23
Do you have installed Emerald theme manager?

---

### Post by BetaMaster on 2006-12-24
Yeah, I do.

---

### Post by hanzomon4 on 2006-12-24
[LIST=1]
[*]Try this login a let the system hang or whatever.
[*]Then switch to a tty **Ctrl+Alt+F1**
[*]Login and use this command ```
top
```
[*]Look to see if compiz is running.... if so press **q** and issue this command ```
killall compiz
```
[*]Switch back to the gui** Ctrl+Alt+F7** and see if it's working
[/LIST]

I installed  compiz  to try it out and beryl manager started loading compiz instead of beryl. This would cause my desktop to freeze on login

---

### Post by BetaMaster on 2006-12-24
I haven't installed compiz though?

I'll try out what you suggested anyway.

---

### Post by hanzomon4 on 2006-12-24
I you don't have compiz installed check to see any if app(perhaps beryl) to see if it's eating all of your cpu usage(It will be the app at the top of the list)

---

### Post by BetaMaster on 2006-12-24
Well I figured it out. It was actually trying to use Compiz, even though Compiz wasn't installed, hence the error. THank you! I've fixed the problem

---

