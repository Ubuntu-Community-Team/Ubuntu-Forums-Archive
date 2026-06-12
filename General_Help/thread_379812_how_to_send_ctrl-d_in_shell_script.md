---
title: "how to send ctrl-d in shell script"
date: 2007-03-08
forum: General Help
---

### Post by jokr004 on 2007-03-08
quick question, how can I send ctrl-d with a command as apposed to with an actual keyboard?

---

### Post by Jmccaffrey on 2007-03-09
The ascii code for EOF(ctrl+D) is 0x1A, you can send this many ways, one way would be this:
```
perl -e "print \"\\x1A\";" | blah_command_to_recieve_it
```

---

