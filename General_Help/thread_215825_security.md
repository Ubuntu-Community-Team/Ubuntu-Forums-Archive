---
title: "security?"
date: 2006-07-14
forum: General Help
---

### Post by galileon on 2006-07-14
hello everyone,

i was reading on zdnet about the latest m$ powerpoint flaw, and people were discussing about security stuff - someone mentioned something i've thought for some time:

i have seen claims about linux being secure because of the privilidges model - eg: if a user runs a binary which is meant to harm his computer, he can only hurt his computer as far as his own privilidge allows, but not bring the whole system down.

but now, say its a single user system (like most desktops i'd say), and that the user is visiting a certain website, and lets suppose also that there is a flaw in firefox/konqueror that allows for execution of arbitrary code or maybe he has just run a program he downloaded or an attachment from Evolution email

so what happens now? this program is now running with the user foo's priviledge - can it not wipe his /home/foo folder? or delete all .odt documents from it?

how does linux handle this? i'd like to know, because i like to bash against windoze with my friends and i use exclusively linux since about a month now...

thanks a lot people,

galileon.

ps: i've seen mentions about sandboxes, which seems to be a generic name to anything that isolates a program from the os eg java virtual machine, or IE7 virtualisation thingy - but is it possible to use this technique against firefox or Evolution? or any program the user runs (as non root at least)?

---

### Post by kripkenstein on 2006-07-14
That's true. If a virus/worm/whatever enters a system, and has a user's privileges, then it can wipe that user's files. What the virus **can't** do is wipe or corrupt the operating system itself, so it can't install a rootkit for example. But - generally the most important data on a computer are data files belonging to the user...

So, the Linux (Unix, really) security model isn't a perfect solution here. It does help, though, by protecting the OS. Also, Linux has other things going for it in the security area - the code is open, so it has been reviewed more, for example.

---

### Post by az on 2006-07-14
[QUOTE=galileon;1255890]
how does linux handle this? i'd like to know, because i like to bash against windoze with my friends and i use exclusively linux since about a month now...

[QUOTE]

It handles it the same way.  You can probably say that linux has fewer security holes which lead to arbitrary code execution in the first place.

The user priviledges model is implemented in Windows and has been for some time.  People chose not to use it and do everythig as administrator.  As well, arbitrary code execution or exploiting other vulerabilities like buffer overflows (smashing the stack) can give you root access, so to say that linux is not vulnerable to that is not true.

---

### Post by aysiu on 2006-07-14
I think you bring up a good point which often gets left out of discussions like this.

What you need to do is regularly back up your files.

---

