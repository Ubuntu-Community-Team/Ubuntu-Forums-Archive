---
title: "Question about 'Spaces' style virtual desktops in Ubuntu"
date: 2007-10-26
forum: General Help
---

### Post by ssmK on 2007-10-26
Hey folks, just a quick n00b question here...  So I installed Ubuntu 7.10 without an active internet connection, it booted up and I noticed a virtual desktop feature similar to the one found in OS X Leopard (which is being released tomorrow).  I noticed I could drag a window to the right, and it would slide to the next desktop over with a virtual desktop indicator overlay that would temporarily appear in the center of the screen.

To fix a problem with the ATI restricted drivers, I reinstalled with an active internet connection, but now this feature is nowhere to be found.  I was wondering if anyone knows how to get it back :confused:

Thanks!

---

### Post by maharbA on 2007-10-26
It sounds like you had "Desktop Effects" when you first installed (congrats, BTW, ATI cards usually fight Desktop Effects). When you used a different driver you may have disabled them, which means you don't get the drag-n-drop feature anymore (are you talking about dragging a window to the right-hand side of the screen?)

Do you still see a workspace switcher in your panel? (it looks like two or more boxes in your panel/taskbar)
OR what happens when you hit ctrl+alt+rightarrow? (try that with some windows open)

You probably still have virtual desktops, just not that easy drag-n-drop feature. (to move an open window to another workspace, try hitting shift+ctrl+alt+rightarrow or leftarrow)

---

### Post by ssmK on 2007-10-26
Thank you so much for the reply, maharbA.  I actually looked into into it some more, and it looks like the issue is exactly what you said ...I had to do some fiddling with drivers, restarted X a couple of times, but I have it working now, yes, it was the desktop effects.

I'm getting the impression that nVidia and Linux play together a bit nicer? :)

---

