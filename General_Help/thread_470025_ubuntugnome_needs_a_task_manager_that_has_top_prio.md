---
title: "ubuntu/gnome needs a task manager that has top priority over all else, because..."
date: 2007-06-10
forum: General Help
---

### Post by bishop9226 on 2007-06-10
every now and then, like windows, all the programs stop responding, even the taskbar/menus and nothing works.  all you can do is move the mouse, you cant kill an app or anything.  this happens when firefox hangs from loading a page sometimes.  so i have my sys monitor bound to ctrl-alt-delete but its really an inferior sys monitor to windows because in windows i can press that and even if nothing else is responding, it will pop up and i can kill tasks.  in ubuntu/gnome, if i want to kill a task i need to somehow be able to click with the mouse or type something in terminal, but if i cant even get terminal open (alt f1, alt f2... doesnt work), then i am left with no choice but to reboot.

---

### Post by Shazaam on 2007-06-10
Have you tried Control-Alt-Backspace? That should dump you back to a login screen.

Right click your panel, choose "Add to Panel". Scroll down to "Desktop and Windows". Highlight "Force Quit". Click Add. Whenever something locks up click the panel icon for Force Quit  and a box will pop up. Follow the instructions and it should work.

---

### Post by nqsonk9 on 2007-06-10
Hmm, i think Gnome taskmanager (or sys monitor as it propre name) works pretty well. With it opened, every non-responding 's no problem for me.

But if you're still looking for some ways to terminate those hang-out process, try ***force quit*** (found in G panel) or ***xkill*** (command easily via terminal or Run box)

---

### Post by nqsonk9 on 2007-06-10
Yeah, Ctrl-Alt-Backspace works fine too in your case. 

But I usually get my Ubuntu restarted if use this command more than 2 times ... wonder ?

---

### Post by harty83 on 2007-06-10
> **bishop9226 said:**
> (alt f1, alt f2... doesnt work), then i am left with no choice but to reboot.

Not for sure if this was a typo, but it should be ctrl-alt-f1 to switch to a new console.  Then ctrl-alt-f7 or f8 to get back to your gnome session.

---

### Post by angryhomer17 on 2007-06-10
> **harty83 said:**
> Not for sure if this was a typo, but it should be ctrl-alt-f1 to switch to a new console.  Then ctrl-alt-f7 or f8 to get back to your gnome session.

You can use Ctrl+Alt+f1 through f6 to get new consoles. f7 will bring you back to your gui, f8 will show the tail of the login output. f9 through f12 don't do anything..........I'm just basing this off of my setup. So, at least for me, it's not a typo.

---

