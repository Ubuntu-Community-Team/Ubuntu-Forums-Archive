---
title: "[SOLVED] Crontab - Can't get it to work"
date: 2007-07-24
forum: General Help
---

### Post by onegreenparker on 2007-07-24
Hello,
I just can't get crontab to do anything.
For example:

<code>
32 02 * * *     export DISPLAY=:0 && xmms -p
</code>

doesn't start XMMS.

What else needs to be done to make use of crontab?

Also, a description of all the items in the above line might give me a clue, eg. what on earth does && do?

---

### Post by Mr. C. on 2007-07-24
How did you add your crontab entry?
Which file, and where?

You can set environment variables ahead of the command, as in :

```
DISPLAY=':0' xmms -p
```

This sets and exports them for that command only.  The && (a logical AND) means "run and evaluate the following command if the previous command succeeded". 

MrC

---

### Post by onegreenparker on 2007-07-24
Simply entered crontab in terminal, this, I believe will edit the users crontab.

---

### Post by onegreenparker on 2007-07-24
Doh!
Also helps to enter the command in the correct case!
xmms worked where XMMS did not

---

### Post by Mr. C. on 2007-07-24
In the future, don't share your interpreted output; instead post the raw data.  What you said you did, and what you actually did were two different things.

In addition, "Simply entered crontab in terminal..." makes no sense.  If you typed "Simply entered crontab in terminal" on the command line, you'd get an error.   You either used an editor and created a file, or used crontab -e, or used a shell redirect such as cat >> crontabfile.  We can't know which, and how you created the file is important.

MrC

---

