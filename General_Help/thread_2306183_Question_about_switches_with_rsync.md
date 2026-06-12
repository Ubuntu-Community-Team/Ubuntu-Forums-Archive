---
title: "Question about switches with rsync"
date: 2015-12-13
forum: General Help
---

### Post by nzdreamer55 on 2015-12-13
Hi everyone

The man page for rsync says the following

  -I, --ignore-times          don't skip files that match size and time
            --size-only             skip files that match in size
            --modify-window=NUM     compare mod-times with reduced accuracy

so do I do ti like this
```
rsync -I --size-only
```

or can I just do this
```
rsync --size-only
```

---

### Post by papibe on 2015-12-13
Hi nzdreamer55.

They are not the same. There's a more detail explanation of both options if you keep reading down the man page.

**--size-only** will only check sizes and ignore times.

**-I, --ignore-times** will disable both, thus marking all files for transfer. (regarding of the confusing naming of the option).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by nzdreamer55 on 2015-12-13
so I need to know if I need to include the -I when choosing --size-only

---

### Post by oldfred on 2015-12-13
I lose track of what settings mean, so I include that in my rsync.

#!/bin/bash
# backup script - mybackup.sh
# a - archive, retain file settings equals -rlptgoD (no -H,-A,-X)
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
# -l, --links copy symlinks as symlinks
 
  example of my /home command, but I run several others and system documentation comamnds:
rsync -aurvlP --exclude-from=mybackup_excludes.lst /home /mnt/backup

The excludes is for temporary files, so they are not backed up.

---

### Post by nzdreamer55 on 2015-12-15
I feel like I am asking the wrong question because the replies that are coming back while informative are not getting at my problem.

So let me try again.

rsync has 2 types of switches.  One is a "-" followed by a letter.  The second is "--" followed by a short word or words.  None of the "--" type switches can be confused with each other.  So do I need to use the first switch and the second switch or can I just use the second switch.

Thanks

---

### Post by Dennis N on 2015-12-15
> **nzdreamer55 said:**
> I feel like I am asking the wrong question because the replies that are coming back while informative are not getting at my problem.

So let me try again.

rsync has 2 types of switches.  One is a "-" followed by a letter.  The second is "--" followed by a short word or words.  None of the "--" type switches can be confused with each other.  So do I need to use the first switch and the second switch or can I just use the second switch.

Thanks

Use the form with the double dash (--), BUT if one of those has a single letter short form shown before it on the same line of the man page, this can be used instead of the -- form.

Also when they exist, you can combine the short forms into one option -rtv for example.

---

### Post by nzdreamer55 on 2015-12-15
> **Dennis N said:**
> Use the form with the double dash (--), BUT if one of those has a single letter short form shown before it on the same line of the man page, this can be used instead of the -- form.

Also when they exist, you can combine the short forms into one option -rtv for example.

So if I understand you correctly. I do not need to use the "-" switch if there is a "--" switch.

---

### Post by Dennis N on 2015-12-15
If both are there, just use one or the other.

---

### Post by nzdreamer55 on 2015-12-15
Thanks

---

