---
title: "How do I change the Icon of a program differently from normal methods?"
date: 2013-06-15
forum: General Help
---

### Post by JJossie on 2013-06-15
I installed a program (Netbeans 7.3) from the provider's website (netbeans.org), rather than from the software center (the copy in the software center is outdated and not as stable). For some reason, the program's icon is really pixelized. It shows up in the dash, the launcher, and the desktop normally, but the icon is ugly and annoying because of the really bad quality. I researched how to change a normal program's icon, and I was told several times to go to /usr/share/applications and change the icon of the file in there. However, Netbeans does not show up in that directory. I looked through other places in /usr/share/ that had icons and found nothing for Netbeans. 
I also tried creating a desktop shortcut, changing its icon, then locking that to the launcher, but it won't stay locked for some odd reason.  
How can I fix this?

---

### Post by Isamu715 on 2013-06-16
Move the desktop shortcut you created to *~/.local/share/applications*(create the directory if it doesn't exist). The shortcut should show up in the Dash as any other app and there should be no problem locking it to the launcher.

---

### Post by sum1nil on 2013-06-16
It might be in '/usr/local/share/icons/hicolor' directory. Take a look there.

---

### Post by JJossie on 2013-06-18
Thanks! actually, I found it was already there and I just changed the icon. I just didn't know about /.local/share/applications.

---

