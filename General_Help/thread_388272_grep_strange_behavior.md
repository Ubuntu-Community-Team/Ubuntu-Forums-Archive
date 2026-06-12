---
title: "grep strange behavior"
date: 2007-03-19
forum: General Help
---

### Post by theOtherMarino on 2007-03-19
I'm running an up-to-date ubuntu. I'm trying to use grep to extract patterns from files and... it does not work on my terminal, while it works on my old debian system....

The command is  :

grep -oR "\w+@" *.html

The "+" sign makes the command has no answer, while :

grep -oR "\w@" *.html

...returns hundreds.

I tried and tried. It  works on Debian but does not on ubuntu.

Crap! Has anyone experienced the same problem?

---

### Post by theOtherMarino on 2007-03-19
Found the answer ... in the man page.

 " In  basic  regular expressions the metacharacters ?, +, {, |, (, and ) lose their special meaning; instead use the backslashed versions \?, \+, \{, \|, \(, and \)."

Okay, I'll RTFM next time. I still wonder why it works on debian without backslash...

---

