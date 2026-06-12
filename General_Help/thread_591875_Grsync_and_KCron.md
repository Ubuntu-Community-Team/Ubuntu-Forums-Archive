---
title: "Grsync and KCron"
date: 2007-10-25
forum: General Help
---

### Post by malel on 2007-10-25
I have been using 'Grsync' to backup my /home directory to an external Hard Drive but I found a nice Gui program called 'KCron' so decided to us that to schedule the 'Grsync' to run say once a week but when I tested it out found that KCron does not make 'grsync' run . I have pointed KCron to  /usr/bin/grsync and would have thought that would have got it going . Can someone please help as it seems I may have pointed KCron to the wrong place . Thank you

---

### Post by por100pre1 on 2007-10-25
Try this:

```
grsync -e default
```

use the name of the Grsync session name you want to use instead of "default".

---

### Post by malel on 2007-10-25
Thank you for that but where does that put the backup? I ran it calling the 'default' backup but don't know where it went to .

---

### Post by por100pre1 on 2007-10-25
Open Grsync use the settings you usually use and then save in **Sessions** using any name you want. Now be sure to use that name in the previously posted command instead of *default*.

---

### Post by malel on 2007-10-25
Thank you again . I have done that as you said but what I want to know is where does it end up after I have run "grsync -e homebckup" ?
I wanted to get 'KCron' set up so that it would run 'grsync" at given intervals. I have tried but although I can run 'grsync' manually I want to run it automatically via 'KCron' .

---

### Post by por100pre1 on 2007-10-25
It should end up wherever the "homebckup" session in Grsync saves its backups. You should have set it up that in Grsync. Now try adding the grsync -e homebckup command to KCron, I haven't tried KCron but I think I should work. That grsync command should start gsync, do the backup, and close grsync.

---

### Post by malel on 2007-10-26
Thankyou very much for your help . I now have 'KCron' up and running properly

This thread may now be considered complete

---

### Post by por100pre1 on 2007-10-26
Glad to help! 8) Please mark the thread as [SOLVED] so it can benefit others. :)

---

