---
title: "[SOLVED] kopete opens links in thunderbird"
date: 2008-01-25
forum: General Help
---

### Post by stanlavisbad on 2008-01-25
Ok, there seem to be a few threads about this, but none of them have worked for me. I'm using kopete in ubuntu (gutsy) (not kubuntu) and links have started opening in thunderbird rather than in firefox. I have checked my web browser is set to firefox and htm, html files are associated with it too. It's not just a kde problem either, as amarok opens links fine. however, KTorrent also uses thunderbird. I've checked in gconf-editor as well. any ideas?

thanks

(before anyone says anything, I prefer KDE applications, but not the desktop environment)

---

### Post by stanlavisbad on 2008-01-28
I posted previously but got no reply, so i'm posting again, because it's a very irritating bug.

i'm using kopete on ubuntu (not kubuntu) gutsy. when i click on links in the message window, or on the email icon for msn, it opens links in thunderbird, rather than firefox. the same happens in Ktorrent, but not in amarok, which opens links in firefox.

html and htm files are associated with firefox and both thunderbird and firefox are default apps for email and web.

please can you give me some ideas, it's very annoying.

thanks

---

### Post by ajgreeny on 2008-01-28
Do you have the kde desktop installed as well as gnome?  I found a similar problem in a previous version of ubuntu on which I added kubuntu-desktop.  In that situation I had to make sure both DE were set to use the same programs for various file types, and if not strange things happened with files opening in one DE's program for some of them but others in the alternative DE's program.  I eventually fixed it with use of kcontrol (kde control center) and setting file associations in that to the same as in gnome.  If you haven't got the whole of the kde desktop, you can certainly install kcontrol as a separate program.  Give it a try;  see if it works.

---

### Post by stanlavisbad on 2008-01-28
hey. that worked. thanks a lot!

---

