---
title: "[SOLVED] problems with &amp;quot;echo&amp;quot; command !"
date: 2007-07-07
forum: General Help
---

### Post by peterx14 on 2007-07-07
Hi all,

I *must* be missing something blindingly obviously, but why doesn't this work:
```
echo --version
```
for me, it just echos the string **--version** !

Thanks!

Peter.

---

### Post by fragos on 2007-07-07
I got the same result, even with "echo --help".  "man echo" said something about shells having their own echo command wich might be different.

---

### Post by xarmian on 2007-07-07
The echo command you're running when you just type "echo" in a bash shell (the default for Ubuntu) is a bash shell command, and not executing the echo executable, which is located at /bin/echo and accepts the options (such as --version) described in widely available documentation..

To execute the non-shell-specific-version, type:

/bin/echo <arguments>

Ex.

/bin/echo --version

-Dave

(edited for typos/errors)

---

### Post by peterx14 on 2007-07-07
Thank you both!! :D

---

