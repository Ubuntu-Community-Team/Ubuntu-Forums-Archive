---
title: "Amarok freezing"
date: 2007-06-02
forum: General Help
---

### Post by skip27 on 2007-06-02
This annoys me like no other, since it happens randomly. Amarok sometimes freezes upon loading, leaving me with this error message:

QPainter::begin: Cannot paint null pixmap

What is going on? I've tried recompiling from the source and reinstalling from the Feisty repo but to no avail. Yet, when I reboot, I can run Amarok just fine. Yet, if I log in/out enough or restart X enough times--usually when I'm experimenting with font configurations--I get this silly message. What gives?

Also--and this happens rarely--Amarok will just freeze when playing a song. Again, this happens rarely, but it's annoying. I'll do a gdb backtrace when it happens and see if I get anywhere.

Aside from that, anyone have a clue?

---

### Post by intMain on 2007-06-02
> **skip27 said:**
> This annoys me like no other, since it happens randomly. Amarok sometimes freezes upon loading, leaving me with this error message:

QPainter::begin: Cannot paint null pixmap

What is going on? I've tried recompiling from the source and reinstalling from the Feisty repo but to no avail. Yet, when I reboot, I can run Amarok just fine. Yet, if I log in/out enough or restart X enough times--usually when I'm experimenting with font configurations--I get this silly message. What gives?

Also--and this happens rarely--Amarok will just freeze when playing a song. Again, this happens rarely, but it's annoying. I'll do a gdb backtrace when it happens and see if I get anywhere.

Aside from that, anyone have a clue?

I don't really know much about Amarok so this can be totally off but I think I read somewhere that for large collections of music Amarok may freeze up.  I think it has to do with the DB Amarok uses.  But again, I haven't been using Amarok so hopefully someone will chime in here.

---

### Post by skip27 on 2007-06-02
Problem solved. After doing a Google search on 'QPaint null pixmap', I came across a website that reported it as a problem regarding kdebase and fonts (aliasing, specifically, but for a DIFFERENT KDE app).

[http://lists.debian.org/debian-kde/2001/11/msg00078.html](http://lists.debian.org/debian-kde/2001/11/msg00078.html)
[http://www.google.com/search?hl=en&q=QPainter+null+pixmap&btnG=Google+Search](http://www.google.com/search?hl=en&q=QPainter+null+pixmap&btnG=Google+Search)

I've been screwing around with my font configuration quite a bit, and only after doing this would Amarok behave this way. I connected the dots and thought of a solution... just needed to wait for the problem to reemerge. So, lo and behold I bumped into this problem again a few minutes ago (the null pixmap issue). Instead of rebooting, however, I ran the following:

sudo dpkg-reconfigure fontconfig-config (redid all my font settings)
sudo dpkg-reconfigure fontconfig
sudo fc-cache -f -v

I logged out and back in, and voila! Amarok runs just fine! Now, I suspect you can get away with just doing sudo dpkg-reconfigure fontconfig and not having to log out, but at this point, I'm not interested in trying all that right now. I'm not sure which step is the critical one, but at least we know now that the solution rests with simply recaching the fonts.

---

### Post by skip27 on 2007-06-06
Nope, nevermind; this didn't do it. God, I hate Amarok.

---

### Post by supaneko on 2007-08-20
UGH... I second that. Having the same issue. If I try to load a large selection of music (such as an entire genre) Amarok will completely freeze. Almost seems like the whole program goes dead but after several minutes (sometimes up to fifteen or twenty minutes, depending on the size of the music I am loading) Amarok will eventually start to work again.

Another issue I have noticed is that if I don't restart my computer for some time, Amarok will freeze when I search for a song. Once I restart, the problem seems to be fine but if I have been running Amarok for a while (usually half a day or longer), it will completely freeze when searching. It doesn't really seem to matter whether or not I am searching for will return a long list of search results, it will always freeze whether one result or a hundred results is expected to come up.

As much as I love the program, I'm not sure how much longer I will be willing to put up with its consistent database problems. :(

---

### Post by strabes on 2007-08-20
Have you guys tried changing the type of database it uses? I think there are three different types. You can choose the type of database on the setup screen when you 1st run amarok.

---

