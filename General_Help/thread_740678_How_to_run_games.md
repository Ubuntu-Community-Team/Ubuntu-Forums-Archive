---
title: "How to run games"
date: 2008-03-31
forum: General Help
---

### Post by waterskill on 2008-03-31
How do I run windows games on Ubuntu when they require usage of .bat files? I'm trying to install Age Of Mythology from a forums that I downloaded it from and the crack is in .bat form. :/
If there is no way then where can I get AOM for Linux?

I'm off to bed for tonight guys, if you want to respond to this post just leave the response and I'll look at it first thing tomorrow.

---

### Post by thisiam on 2008-03-31
install Wine, there you go first one to say it but honestly i would just dual boot and use windows when playing games made for windows only.

---

### Post by waterskill on 2008-03-31
> **thisiam said:**
> install Wine, there you go first one to say it but honestly i would just dual boot and use windows when playing games made for windows only.

Wine doesn't run .bat files does it? And I cant dual boot on mine. Well I can, it's just I only have 40g of memory on it and 900m of ram so it would be kind of stuffed/laggy.

---

### Post by HunterK on 2008-03-31
Open the .bat file in a text editor and see what exactly it was written to do.  Maybe all it does is run an EXE.   If so, you could probably run that same exe in Wine? :confused:

---

### Post by danwood76 on 2008-03-31
Run it in dosbox or dosemu.
I installed a patch (update) for theme hospital that way and it should work fine.

---

### Post by malfist on 2008-03-31
A batch (.bat) file is only a list of command line instructions for windows. Open up the ubuntu terminal and execute the lines with wine prefixed infront of them. That should fix most of it. If it uses control statements (if/while/for) you may have to rewrite it or figure out what to do. It's not that hard. If you can't do it, post the batch file and someone can probably convert it for you. I would point out that wine isn't the best to play games on, but WoW does good enough.

---

### Post by waterskill on 2008-03-31
Ok, do you want me to post the words in the file or just the whole file itself?

---

### Post by monraaf on 2008-03-31
Try: **wineconsole** *file.bat*

---

### Post by waterskill on 2008-03-31
Perhaps I should just wait till I'm more experienced until I try and play games x.x

---

