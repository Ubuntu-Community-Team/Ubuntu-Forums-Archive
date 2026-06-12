---
title: "Katapult Problem: alt+space no longer working!"
date: 2007-04-03
forum: General Help
---

### Post by bg1256 on 2007-04-03
I adjusted my session settings so that KDE starts with a fresh session everytime.  However, once I did that, Katapult no longer launches by pressing alt+space!

If I go to Kmenu -> utilities -> katapult it works fine.  

And under global shortcuts, alt+space is still dedicated to katapult.

I have since changed my session settings to restore a previous session, but it hasn't fixed the problem.

Any help would be appreciated.

edit:

I changed the shortcut so that win+space would be secondary, and it launches katapult; however, I am accustomed to using alt+space, and it would be nice to get it working again.

---

### Post by MartinJ on 2007-04-03
Since you are starting with a new session, Katapult isn't loaded.
Two options: go back to the 'save session' option; or add a shortcut to Katapult in your ~/.kde/Autostart directory

Not at my own pc at the moment so can't check the details of this.

---

### Post by bg1256 on 2007-04-03
It seems that setting KDE to restore the session solved the problem.

And messing with the global shortcuts got alt+space working again as well.

Problem solved.

---

### Post by airjaw on 2007-12-05
Sorry but I don't think this issue should be closed.
I still have issues with Katapult daily (on Gnome).
Alt+space will stop working all of a sudden, but CTRL+Space will work when I set it.
Relaunching katapult doesn't help; changing the global variables around doesn't help.
Something is broken.

---

