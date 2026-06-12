---
title: "How can I add &quot;quote symbols&quot; before email text?"
date: 2013-04-11
forum: General Help
---

### Post by d0006 on 2013-04-11
I'm looking for a text editor that will allow me to "prepend" a quote symbol to email text, i.e., add a > before every line of selected text.  I looked around and could not find a way to do this in gedit.  Please post if you know of an editor that can do this.

Thanks

---

### Post by tornadof3 on 2013-04-12
Use regular expression searches in eg GEdit:

With some text that spans several lines in Gedit, go to Search -> Replace (Ctrl-H)
search for:     \n
replace with:   \n>

worked just fine when I tried it now...

---

### Post by d0006 on 2013-04-15
Thanks. Unfortunately, this only works with hard carriage returns after each line (newline - \n).  It does not work if the lines are wrapped.

---

