---
title: "Sudoers and disable require tty for particular user"
date: 2012-11-19
forum: General Help
---

### Post by JackTheKnife on 2012-11-19
How can I disable require tty for particular user in sudoers?

Thanks

---

### Post by Lars Noodén on 2012-11-19
Just a guess, I haven't tested it, but could you do something like this?

```

User_Alias SOMEGROUP = foo, bar
Defaults:SOMEGROUP      requiretty = 0

```

But isn't **requiretty** already off by default?

---

### Post by Lars Noodén on 2012-11-19
For some reason the example above does not work.  I think something is wrong with the manual page or with sudo.  

This should work for an individual user. But again, requiretty is off by default.

```

Defaults:jacktheknife  !requiretty

```

---

### Post by JackTheKnife on 2012-11-20
My question is related to that topic: [http://ubuntuforums.org/showthread.php?t=2085994](http://ubuntuforums.org/showthread.php?t=2085994) and no clue how to deal with it :(

---

### Post by Lars Noodén on 2012-11-20
What do you do to get the error message?  Can you show the complete error message and the programs leading up to it?

---

### Post by JackTheKnife on 2012-11-21
> **Lars Noodén said:**
> What do you do to get the error message?  Can you show the complete error message and the programs leading up to it?

TortoiseSVN. Also I have updated OP with my post-commit hook and sudoers from 11.04. Now I'm trying to get this split piece by piece to find out what is going on :\

---

