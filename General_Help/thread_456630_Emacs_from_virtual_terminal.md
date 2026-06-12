---
title: "Emacs from virtual terminal"
date: 2007-05-27
forum: General Help
---

### Post by BobvanderPoel on 2007-05-27
For some reason I can't get my emacs working in a VT. It works just fine under X, but when I try to run in a VT (linux console) I get:

emacs: cannot open termcap database file

I do have termcap stuff installed.

the TERM variable is set to "linux"

there is an entry in /usr/share/terminfo/l/linux, a link to /lib/terminfo/l/linux which also exists.  Permissions appear to be okay.

My emacs is GNU Emacs 22.0.95.2 I complied this myself. Doing an ldd on the binary doesn't show an missing libs.

Not sure what to try next. Thanks.

---

### Post by spin2cool on 2007-05-28
Double check to make sure that you have 'termcap-compat' and 'libncurses5-dev' installed.  (I've also read that you may have to recompile emacs after installing libcurses5-dev)

---

### Post by BobvanderPoel on 2007-05-28
Never occurred to me to recompile :) But, I figured I'd give that a go ... same problem.

Oh, what's this about ncurses-dev ... blush ... not installed. So, I grabbed ncurses-dev (which I assume has the correct header files) and recompiled emacs again (thank the guys at Intel and AMD for fast processors ... I remember when this took hours, not minutes).

Now, it works just fine! Thanks for the pointer.

I have no idea why compiling without the -dev stuff would even work! No errors in compile or in the configure. Is that a bug or is emacs desgined to work without terminal support?

Also, I have no idea about termcap-compat. Doesn't come up in synaptic packages. Probably swallowed into something else?

Anyway, emacs now works. Now, on to fix other problems!

---

### Post by spin2cool on 2007-05-28
Beats me - I just did a qucik google search using our error message and found a few likely solutions (all on the first page of results).  Don't forget about google next time you need an answer ;)

---

### Post by BobvanderPoel on 2007-05-28
> **spin2cool said:**
>   Don't forget about google next time you need an answer ;)

Funny thing about the google suggestion is that I did that :) But, of course, I made it way too complicated ... never figured to just search for the complete error message ... instead I had some silly combination of emacs and terminal, etc. 

Lesson here: always do the simple things first!

---

