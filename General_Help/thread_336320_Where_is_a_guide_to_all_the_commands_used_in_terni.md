---
title: "Where is a guide to all the commands used in terninal window?"
date: 2007-01-11
forum: General Help
---

### Post by tc101 on 2007-01-11
Where is a guide to all the commands used in terninal window?  

I want to learn this language.  Lots of people in the forum give each other scripts to copy and paste into the terminal window, but I want to learn to write this stuff myself.  Is there a good online guide, or should I buy a book?

---

### Post by taurus on 2007-01-11
[http://www.oreilly.com/catalog/bash3/index.html](http://www.oreilly.com/catalog/bash3/index.html)

---

### Post by rioghal on 2007-01-11
I like this one:
[http://www.onlamp.com/linux/cmd/](http://www.onlamp.com/linux/cmd/)

---

### Post by Moldz on 2007-01-11
For a quick and usually complete fix, try the man page.  Simple type "man command".  If you want to search the man pages, use "apropos keyword" instead.  Almost every command should have a man page.

---

### Post by tc101 on 2007-01-11
Do you mean to type man and the name of the command in the terminal window?

---

### Post by usien on 2007-01-11
this is a comprehensive tutorial:
[www.linuxcommand.org](www.linuxcommand.org)

---

### Post by tc101 on 2007-01-11
> this is a comprehensive tutorial:
[www.linuxcommand.org](www.linuxcommand.org)

Thanks usien.  I started reading that and I think it is just what I was looking for.  Also, I like the way the guy writes and makes his points.  I feel like he is talking to Me.

---

### Post by bodhi.zazen on 2007-01-11
This one's not bad either:

[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

---

### Post by Moldz on 2007-01-11
> **tc101 said:**
> Do you mean to type man and the name of the command in the terminal window?

Yeap.  For example, if you want to know what the "tee" command does, type this:
```
man tee
```

---

### Post by tc101 on 2007-01-11
> Yeap. For example, if you want to know what the "tee" command does, type this:

Cool

---

### Post by tc101 on 2007-01-11
There is no scroll bar in GNOME Terminal.  I typed man tee, but I could not see the whole description.

---

### Post by majoridiot on 2007-01-11
if you're looking for an excellent one-book investment, check out:

[http://www.amazon.com/Ubuntu-Unleashed-Andrew-Hudson/dp/0672329093/sr=8-1/qid=1168571562/ref=pd_bbs_sr_1/105-5401314-1721243?ie=UTF8&s=books](http://www.amazon.com/Ubuntu-Unleashed-Andrew-Hudson/dp/0672329093/sr=8-1/qid=1168571562/ref=pd_bbs_sr_1/105-5401314-1721243?ie=UTF8&s=books)

it covers pretty much everything, at least as an introduction.  it includes chapters on various
scripting languages as well.  it's a great value at twice the price.

(and no... i'm not secretly the author in disguise. :D )

---

### Post by bodhi.zazen on 2007-01-12
> **tc101 said:**
> There is no scroll bar in GNOME Terminal.  I typed man tee, but I could not see the whole description.

Yes there is ....

Open a terminal

Edit - > profiles -> Hit the Edit box -> scrolling

---

### Post by po0f on 2007-01-12
tc101,

man pages are output through a 'pager', something that let's you scroll through large documents through a terminal instead of outputting all at once.  (Yes some people still use a real terminal and need it.  :))  Just use up and down to scroll through a man page.  You can also hit '/' and a search term to search the man page if you are looking for something specific.

---

### Post by dcstar on 2007-01-12
> **tc101 said:**
> There is no scroll bar in GNOME Terminal.  I typed man tee, but I could not see the whole description.
```
man tee | less
```

And:
```
man -k something-or-other
```
will list all man pages which match "something-or-other"

"man -k" is the same as "apropos", but easier to spell (and remember......)

---

### Post by usien on 2007-01-12
use up/down arrow keys to move one line at a time or the page scroll keys to move a page

---

### Post by tc101 on 2007-01-12
Thanks everybody.  I see how it works now.

---

