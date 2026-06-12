---
title: "A question for some gurus: launching an app from TTY1 and having it open under gnome"
date: 2008-02-28
forum: General Help
---

### Post by Lonergan on 2008-02-28
This question is rather strange but I can't seem to find help on this one from anywhere, even my customary goto guru guys don't have an answer.


I load up Ubuntu, Gnome launches and I log in.  No problems.  X session is in TTY7 or 9 usually.

If I press Alt+F1 I am now in TTY1 and can do some nice things outside of X.  Sometimes though, I would like to test programmes that don't seem to have a log function associated with them, so launching from a non-X terminal and having it run in X would be really nice.

How could I for instance launch Firefox from TTY1 and have it open in TTY7 under gnome?  Is this possible? What about something a bit more simple, launching non-X app from TTY1 and having it run in TTY2?

Thanks in advance.

---

### Post by bodhi.zazen on 2008-02-28
Depends on the application.

you need to specify the display ( it is [noparse]:0[/noparse] )

So you can export DISPLAY=[noparse]:0[/noparse]

or sometimes application -flag [noparse]:0[/noparse]

command -d [noparse]:0[/noparse]

See here for an example :

[http://ubuntuforums.org/showthread.php?p=3816948](http://ubuntuforums.org/showthread.php?p=3816948)

===============================

For non-X apps, use screen

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)

		[http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html](http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html)

	[http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen)

---

### Post by Lonergan on 2008-02-28
Well this is very handy!  Thanks.  This will work perfectly when I'm in Gnome.  However, if I don't have X running at all, does the display option work to send a process to another terminal?  Say from TTY1 to 2?

Thanks again for the link, very good info.

---

### Post by bodhi.zazen on 2008-02-28
No, that is just for X apps, and you need to have X running. You may be interested in a lighter window manager, like *box (fluxbox or openbox).

Screen will allow you to cycle through sessions.

I do not know how to send an app from tty1 to tty2.

See this thread : [http://ubuntuforums.org/showthread.php?t=437607](http://ubuntuforums.org/showthread.php?t=437607)

---

