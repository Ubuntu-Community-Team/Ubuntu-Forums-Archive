---
title: "[SOLVED] Firefox"
date: 2008-04-02
forum: General Help
---

### Post by verby on 2008-04-02
when I try to run firefox it tells me that firefox is alrady running. how to close it and re-open, actually how to view the programs which are running?
and...
when I try to open web page it tells me that i'm offline and doesn't display the page. i'm not offline at least with other programs, how to change it in fireofx or somewhere else?

---

### Post by geraldm on 2008-04-02
```

# view all running processes
ps aux
# find the process running firefox
ps aux | grep "firefox" -
# terminate a process--number 9629--, bash shell
kill SIGTERM 9629

```

The command grep "firefox" -  may return three processes, You only need to terminate the right one ;) 

Gerald

---

### Post by Cope57 on 2008-04-02
You have no Internet at all?

---

### Post by aysiu on 2008-04-02
Press Alt-F2 and paste in ```
killall firefox-bin
``` Then launch Firefox and go to *File* and make sure *Work Offline* is unchecked.

---

### Post by verby on 2008-04-02
file - uncheck work offline

Thank you... that was easy, and I was looking for a while under prefs :)

---

