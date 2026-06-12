---
title: "[SOLVED] terminal"
date: 2007-08-21
forum: General Help
---

### Post by yorkie on 2007-08-21
I am trying to find a file using locate in a terminal all I get is this message

_locate: warning: database /var/lib/slocate/slocate.db' is more than 8 days old_

then returns to command prompt anyone know something about this message
thanks in advance

---

### Post by kerry_s on 2007-08-21
> **yorkie said:**
> I am trying to find a file using locate in a terminal all I get is this message

_locate: warning: database /var/lib/slocate/slocate.db' is more than 8 days old_

then returns to command prompt anyone know something about this message
thanks in advance

sudo updatedb
locate your-file

---

### Post by heimo on 2007-08-21
> **yorkie said:**
> I am trying to find a file using locate in a terminal all I get is this message

_locate: warning: database /var/lib/slocate/slocate.db' is more than 8 days old_

then returns to command prompt anyone know something about this message
thanks in advance

Run 
```
sudo updatedb
```

I think it's scheduled to run every day by default, so there may be something wrong with it or cronjob.

---

### Post by yorkie on 2007-08-21
Thanks that did the trick never seen that command before one to file away for future ref
another problem solved
cheers

---

