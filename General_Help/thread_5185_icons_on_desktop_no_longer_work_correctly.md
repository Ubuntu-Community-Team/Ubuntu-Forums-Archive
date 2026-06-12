---
title: "icons on desktop no longer work correctly"
date: 2004-11-16
forum: General Help
---

### Post by negativ on 2004-11-16
OK, so I just reinstalled Ubuntu...  I installed Firefox 1.0 from mozilla.org and set it up, etc etc.  Now, though, when I save html files from websites for future reference, clicking on them in nautilus results in... nothing.

Well, not exactly nothing...   I get a box that says something along the lines of, 

"Cancel opening foo.html?  To cancel, click cancel"

Waaah!! :sad:   any ideas how to get this working again?  I added "firefox" to the "open with" properties, and the same thing happens....

---

### Post by Crisp on 2004-11-16
Where did you install firefox?  If you just typed "firefox" for open with, nothing will happen, because it's not recognised.  Instead, either type in the full path of firefox, or create a linker in /usr/bin so that "firefox" will be a recognised command.

-Crisp

---

### Post by negativ on 2004-11-16
[QUOTE=Crisp]Where did you install firefox?  If you just typed "firefox" for open with, nothing will happen, because it's not recognised.  Instead, either type in the full path of firefox, or create a linker in /usr/bin so that "firefox" will be a recognised command.
-Crisp[/QUOTE]

I installed firefox in /usr/local/firefox, and created a link to it in /usr/bin (I also renamed the old firefox executable to firefox.old)

I'll try an explicit path when I get home, but right now I can invoke firefox by simply typing "firefox" in a terminal regardless of what directory I'm in, so I have to assume that means it's in the path.

---

### Post by Crisp on 2004-11-16
[QUOTE=negativ]I installed firefox in /usr/local/firefox, and created a link to it in /usr/bin (I also renamed the old firefox executable to firefox.old)

I'll try an explicit path when I get home, but right now I can invoke firefox by simply typing "firefox" in a terminal regardless of what directory I'm in, so I have to assume that means it's in the path.[/QUOTE]
 Yeah that's what I did, although at first I just had my icon on a panel linking to the /home/crisp/blahblah path where I installed it.  Anyway negativ, do that.

-Crisp

---

### Post by negativ on 2004-11-16
nope, still doesn't work.  It worked before I reinstalled, so I have no idea what's different this time.  Hmm...... :-k  ](*,)  :-k

---

