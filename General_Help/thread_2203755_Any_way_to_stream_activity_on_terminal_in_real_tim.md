---
title: "Any way to stream activity on terminal in real time?"
date: 2014-02-04
forum: General Help
---

### Post by Bruce_Strafford on 2014-02-04
Like whatever I'm doing on the computer to be showing up in real time in the terminal?

---

### Post by tgalati4 on 2014-02-04
Your commands are logged in a framework called *history*.

Open a terminal:

```
history
man history
```

With a little scripting and root privilege you could monitor a user in near-real time.  There are network login monitors like *whowatch*.

---

### Post by Lars Noodén on 2014-02-05
If you want to see what the computer is spending its resources on then there are [top](http://manpages.ubuntu.com/manpages/saucy/en/man1/top.1.html) and [iotop](http://manpages.ubuntu.com/manpages/saucy/en/man8/iotop.8.html).

---

### Post by hoopia on 2014-02-05
If you want to monitor logs, you can use tail:

tail -f -n 0 /var/log/syslog

Leave this running and whenever syslog (or any other file you want to monitor) updates, it will appear in Terminal.

---

