---
title: "rsync after a cp"
date: 2006-11-02
forum: General Help
---

### Post by luvdemheels on 2006-11-02
We had been using cp to copy data from one place to another. What happens if we now want to use rsync and the data already exists from a cp copy in the destination??

Do I need to delete the data in the destination first or is rsync smart enough to deal with the data that is there from the cp??

---

### Post by amo-ej1 on 2006-11-02
Nobody has ever died from reading the help section :-D 

```

e@lap:~$ rsync --help 2>&1  | grep del
     --del                   an alias for --delete-during
     --delete                delete files that don't exist on the sending side
     --delete-before         receiver deletes before transfer (default)
     --delete-during         receiver deletes during transfer, not before
     --delete-after          receiver deletes after transfer, not before
     --delete-excluded       also delete excluded files on the receiving side
     --ignore-errors         delete even if there are I/O errors
     --force                 force deletion of directories even if not empty
     --max-delete=NUM        don't delete more than NUM files
     --delay-updates         put all updated files into place at transfer's end
 -0, --from0                 all *-from/filter files are delimited by 0s

```

---

### Post by luvdemheels on 2006-11-02
Thanks for the reply but this doesn't answer my question.

---

### Post by angrykeyboarder on 2006-11-11
> **amo-ej1 said:**
> Nobody has ever died from reading the help section :-D 

```

e@lap:~$ rsync --help 2>&1  | grep del
     --del                   an alias for --delete-during
     --delete                delete files that don't exist on the sending side
     --delete-before         receiver deletes before transfer (default)
     --delete-during         receiver deletes during transfer, not before
     --delete-after          receiver deletes after transfer, not before
     --delete-excluded       also delete excluded files on the receiving side
     --ignore-errors         delete even if there are I/O errors
     --force                 force deletion of directories even if not empty
     --max-delete=NUM        don't delete more than NUM files
     --delay-updates         put all updated files into place at transfer's end
 -0, --from0                 all *-from/filter files are delimited by 0s

```

That doesn't help me either.  RSYNC is overly complex. If Wiley ever publishes "RSYNC For Dummies" I'll be among the first to buy it.

---

