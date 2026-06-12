---
title: "Apps./ windows &quot;Greying Out&quot;?"
date: 2007-12-11
forum: General Help
---

### Post by Sidewinder1 on 2007-12-11
I'm brand new to Linux. GG install about two wks. ago. What is happening when a window greys out and is unresponsive? Once in a while it comes back, but rarely; even if I close other programs. Checked services but couldn't find anything definitive. Shutting down then takes forever. I'm assuming that it's a RAM issue? I have 768 megs of ram system is a Dell 4550, about 4 - 5 years old. Any advice would be greatly appreciated.

  Thanks, Ed

---

### Post by dpar on 2007-12-11
I believe it does that when your processor gets close to 100%.

---

### Post by mcduck on 2007-12-11
It's a feature of Compiz (the "Desktop Effects"). If a program gets frozen, Compiz will desaturate the window to notify you about it.

So the "greying out" is just a signal to tell you that the app is frozen, not part of the problem itself.

Although Compiz does this a bit too easily, sometimes if a program needs a long time to do something Compiz believes that it's frozen and desaturates it's window. This shouldn't be a problem, as soon as the program becomes responsive again Compiz will return the colors.

Usually you can close a frozen program easily by just clicking the x-button in the titlebar, or right-clicking it in the window list and selecting "Close". You'll get a popup telling you that the program mis frozen and asking if you want to force it to close. If that doesn't work, press Alt-F2 and run 'xkill'. This will change your cursor into skull&bones and now you can just click any window to force the program to close.

---

### Post by Sidewinder1 on 2007-12-11
Many, many,... thanks

---

