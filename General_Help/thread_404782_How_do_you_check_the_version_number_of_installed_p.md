---
title: "How do you check the version number of installed programs (software)?"
date: 2007-04-08
forum: General Help
---

### Post by shakma on 2007-04-08
Hello, all.  I really have tried to find an answer for this already posted in these wonderful forums.  So:

How do you check to see what version of a program is already installed on your system.  Specifically, I am now checking to see which "wine" I am running (to answer a question in *their* forums), but this comes up often when installing new software - especially from source.  

For example, when I was installing ntfs-3g (which I later found in the repos :) ), it kept telling me I needed "fuse 2.10" or so... and I didn't know how to see what version I already had... or if I even already had it!

Is there a simple way to check if a *_specific program_* is installed, and, assuming it is, what version it is?

Thanks in advance,
shakma

---

### Post by Bachstelze on 2007-04-08
```
dpkg -l | grep wine
```

You can of course replace wine with every other name you want ;)

---

### Post by shakma on 2007-04-09
Awesome!  Thanks, Hymn. 

Quick follow up:

so, the response to the above code was:

"ii  wine                                       0.9.33~winehq0~ubuntu~6.10-2         Microsoft  Windows Compatibility Layer (Binar"

[B][I]**Hmm... when I post this, it takes the spaces out, but there are a bunch of spaces between "ii wine" and the next part, and "6.10-2" and the Microsoft part.**
[/I][/B]
Is that the name of the file installed?  Is that all one result?

Thanks, again.
shakma

EDIT:  I tried running this command for some other programs and I think I've figured out the syntax.  Any more informed responses would be great, too, though.

---

