---
title: "Java Web Start on Kubuntu"
date: 2006-11-07
forum: General Help
---

### Post by Hikaru79 on 2006-11-07
Hello.

I'm running a fairly new Kubuntu install. I installed Java without any problems, but I do have one minor complaint.

I run several programs through Java Web Start on a very regular basis (gGo and CGoban3 to be exact). Back in Ubuntu (Gnome version), when running a JWS program for the first time, it would ask me if I wanted to make a shortcut to it in the menu and desktop, and I would always answer "yes" because that's much more convenient than going online and finding the link to the program every single time.

However, in Kubuntu, no such option is presented. It loads the JWS programs fine, but every time I want to re-run it I have to either go back to the sites or to the "Sun Java 5.0 Web Start" menu entry in "Internet", and then select it from the list. It also makes it impossible to set CGoban3 as my default .sgf editor (something I COULD do in Gnome).

So, does anyone know if there's a way to make it prompt me for shortcuts? Through the Java Control Panel perhaps? (Something which was in System->Administration in Gnome, and not visible for me at all in KDE)?

Thanks in advance :)

---

### Post by Absorbed on 2007-07-05
Typing "javaws http://files.gokgs.com/javaBin/cgoban.jnlp" at a command prompt opened CGoban3 for me. If you make an icon on your desktop or menu with that command, I imagine it will work.

---

### Post by Hikaru79 on 2007-07-05
> **Absorbed said:**
> Typing "javaws http://files.gokgs.com/javaBin/cgoban.jnlp" at a command prompt opened CGoban3 for me. If you make an icon on your desktop or menu with that command, I imagine it will work.

Thanks for the reply :)

Of course, that was the first thing I tried, but it doesn't help. Removing the cached entry from the Java WS control panel, rebooting, and trying again seems to work some of the time ... for the first launch only, and then it fails to validate again.

I can't quite figure out the pattern behind the failures. Luckily my Macbook Pro is back from service now, where this problem does not surface. The computer this problem occurred on was mostly a server anyway.

If anyone knows of a solution, however, I'd still be very interested in hearing about it, even if just for curiosity's sake.

Thanks!

---

