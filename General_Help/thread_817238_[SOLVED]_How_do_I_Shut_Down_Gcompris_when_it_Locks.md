---
title: "[SOLVED] How do I Shut Down Gcompris when it Locks Up the Computer"
date: 2008-06-03
forum: General Help
---

### Post by tuebinger on 2008-06-03
I have Edubuntu running in my classroom .  The only problem is that the computers lock up occasionally when running the Educational Suite Compris, and since this program takes up the whole screen I can't get to the system monitor to end the process.  Is there a way to shut down this program when it locks up the computer?

---

### Post by latna on 2008-06-03
Assuming you still have use of the mouse and/or keyboard, there are a couple options.

You could try pressing ctrl+alt+escape and see if that works. That starts xkill and you can kill a gui app by clicking anywhere in it's window.

If that doesn't work you can try pressing ctrl+alt+F1 to switch to a console. Just log in and kill the process from there.

If you lose the keyboard and mouse, you could set up ssh and kill the process remotely. If it's so locked up you can't access it from the network, you might be outta luck unless someone else has any other ideas.

---

### Post by tuebinger on 2008-06-04
Thanks for the tips!  I will try these next time one of the computers locks up again.

UPDATE

Gcompris froze on one of the computers the other day, so I used Ctrl+Alt+Escape (actually didn't start xkill) but it allowed me to access the menu so I can shut down gcompris using the system monitor.

Thanks!

---

