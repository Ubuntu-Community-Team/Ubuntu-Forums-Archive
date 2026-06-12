---
title: "Logout KDE using console"
date: 2008-06-06
forum: General Help
---

### Post by PasiM on 2008-06-06
Is it possible to logout Kubuntu using some commandline command? So that computer would return to that Kubuntu login screen just like when selecting logout from K Menu.

And I really mean logout, no shutdown or reboot. That seems to be easily done with **/sbin/reboot** or **/sbin/shutdown** commands.

I already found out that in Gnome logout could be done like this **/usr/bin/gnome-session-save --kill --silent**. I'm quite sure there's some sort similar command for KDE?

---

### Post by pretzelkid on 2008-06-25
I've been looking for the same command for a couple of days now, if I find anything I'll post...in the meantime...
Anyone know the answer?

---

### Post by pretzelkid on 2008-06-26
Funny how I found this after posting. It's from an irc log:
[http://irclogs.ubuntu.com/2006/07/05/%23kubuntu.html](http://irclogs.ubuntu.com/2006/07/05/%23kubuntu.html)

Here's the gist of it...
12:18	uniq	d4m4ge: you want a command to write in konsole, that executes a logout similar to kmenu -> logout?

12:18	D4m4ge	uniq exactly :)

12:21	uniq	d4m4ge: try 'killall kdeinit' to logout KDE.

12:23	D4m4ge	thx uniq i'll try it in a few minutes

12:24	uniq	d4m4ge: there is also 'dcop kdesktop default logout' you can try.

12:27	uniq	d4m4ge: you can also try 'dcop ksmserver ksmserver logout 0 0 0 '. If you want to reboot the machine after logout you have 'dcop ksmserver ksmserver logout 0 1 1'

12:27	D4m4ge	ok thanks
12:28	uniq	the killall example is the ugliest. the dcop ones are more elegant. depending on what you want.

12:28	D4m4ge	uniq i want the cleanest way to delog, otherwise ctrl+alt+backspace works well, but i'm afraid it's a bit brutal...

I haven't tried any of these yet, I'm running Mythbuntu 8.04 and need it for a shutdown script.

---

