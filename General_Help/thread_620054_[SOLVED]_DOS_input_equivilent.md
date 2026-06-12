---
title: "[SOLVED] DOS input equivilent"
date: 2007-11-22
forum: General Help
---

### Post by garyj1972 on 2007-11-22
I have created a desktop icon to run a terminal command. It's NETSTAT with a few attribs that I can never remember.

When I run it. I see the window pop-up run and disappear. But Linux is so damned fast I don't get time to see it never mind read it.

In DOS I would have used some kind of input prompt to hold the screen open, but as a newbie in Linux I'm not sure how best to approach this.

Any ideas?

Thanks in advance

Gary

---

### Post by WakkiTabakki on 2007-11-22
You can use a "pipe" to send the output of one command to another program... less is a program that shows text page by page, so try
```
netstat | less
```

/N

---

### Post by garyj1972 on 2007-11-22
thanks but no joy, still dies immediately. Gary

---

### Post by garyj1972 on 2007-11-22
found a solution
created small script with read command at the end to hold it open until key press

Thanks for help

Gary

---

