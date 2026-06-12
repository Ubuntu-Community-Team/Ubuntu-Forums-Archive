---
title: "Is there a log file for GNOME commands?"
date: 2012-11-04
forum: General Help
---

### Post by zozza on 2012-11-04
I am wondering if there is a log of what I type in the GNOME terminal.

I am not talking about 'history' which has a finite recording capacity but if there is a specific log file which records all entries.

Thanks!

---

### Post by Habitual on 2012-11-04
No.

---

### Post by ibjsb4 on 2012-11-04
You could script it

[http://www.google.com/search?q=script+to+log+terminal+session+commands+linux&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=script+to+log+terminal+session+commands+linux&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

Edit: Got a better hit here

[http://www.google.com/search?q=script+to+log+terminal+session+commands+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=script+to+log+terminal+session+commands+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by Cheesemill on 2012-11-04
You can edit the HISTSIZE and HISTFILESIZE values in your ~/.bashrc file so that the history contains more entries, just set them to something very large and you will effectivley have an unlimited history.

---

