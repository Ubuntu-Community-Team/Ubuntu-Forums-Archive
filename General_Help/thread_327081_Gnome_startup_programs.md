---
title: "Gnome startup programs"
date: 2006-12-28
forum: General Help
---

### Post by klayn on 2006-12-28
Hi all,

I want gdesklets to startup when I log in, but when I add it to the list in System -> Preferences -> Sessions and restart the computer, it doesn't start up. When I check if it's there after reboot, it's not in the list of startup programs. All of the other programs (gnome-power-manager, volume manager, etc) are still there. 

I think this may be some kind of a permission issue, e.g. some file's permissions got changed that controls this list. The problem is, I don't know where to look. Any suggestions?

Thanks in advance.

---

### Post by ronin69hof on 2006-12-30
I have the same problem.  I put beryl-manager in my sessions/startup programs and after a reboot or logout its gone.

---

### Post by peekj on 2007-01-18
I had the same problem with beryl and other apps. Here's my workaround:

Go to the *~/.config/autostart/* folder.

Create a new *beryl-manager.desktop* file. Might have to *sudo* that.

Enter the following contents and log out and back in. Voila.

```
[Desktop Entry]
Name=beryl-manager.desktop
Encoding=UTF-8
Version=1.0
Exec=beryl-manager
X-GNOME-Autostart-enabled=true
```

---

### Post by anfauglir on 2007-02-13
Actually the real solution for that is to chown the autostart directory. the reason that the sessions proggie cant save that file by itself is that the dir is owned by root. i'm pretty sure that this is a bug actually from installing beagle and glipper (in my case those two programs had shortcuts in there, and both were owned by root) the moment i did a chown myuser:myuser on the dir, i was able to save everything without creating the shortcut file by hand.:guitar:

---

