---
title: "[SOLVED] Symbol help in manual"
date: 2008-05-20
forum: General Help
---

### Post by prowi on 2008-05-20
How do I get Linux manual help on non-word commands, for example on the dollar sign, asterisk, and square brackets?

---

### Post by bingoUV on 2008-05-20
Don't know what you mean by linux manual help, but if you mean shells , terminals and terminal emulators read [http://www.vias.org/linux-knowhow/lnag_05_05_09.html](http://www.vias.org/linux-knowhow/lnag_05_05_09.html) 

These are not commands, but might have important meaning to the shell or the terminal.

On the other hand, if you are having problems viewing special characters in man pages, see try pinfo instead of man. Or, post the output of the following command
```

echo $LANG

```

---

### Post by prowi on 2008-05-20
Yes, perfect.  Thanks.  So these are dependent on the shell I'm using?

---

### Post by bingoUV on 2008-05-21
Yes, they are dependent on the shell. But there is a lot in common between different shells. If you know something in one shell, it is worthwhile to try it in another shell too before looking for specific documentation. 

This link gives information about bash, the most popular of shells.

---

