---
title: "Where is my shutdown logfile located?"
date: 2014-10-26
forum: General Help
---

### Post by prisoner8492 on 2014-10-26
I'm getting an important message during shutdown and can't find the logfile which contains shutdown and/or startup log messages.

I've grep'd a string in the message from my "/var/log/syslog" file and used "grep -nr "string" within "/var/log/", also to no avail.

NOTE: Added Xubuntu as thread prefix, but assume it's the same regardless of desktop environment.

---

### Post by nerdtron on 2014-10-26
hhhhmmm just passing by...how's the case of the string? lower case? upper case? you can try adding the option -i on the grep command.

how about the /var/log/kern.log?

```
grep -nri "string" /var/log/*
```

---

