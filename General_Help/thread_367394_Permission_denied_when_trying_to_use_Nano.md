---
title: "Permission denied when trying to use Nano???"
date: 2007-02-22
forum: General Help
---

### Post by Maelgwyn on 2007-02-22
Hey guys,

as I'm using Fluxbox, I don't have Kate or Gedit or anything like that installed as an editor for my config files, and when I try to ```
nano .fluxbox/init
``` I get the following error:

```
Error reading /home/hakuturi/.nano_history: Permission denied

Press Enter to continue starting nano.
```

Is it safe for me to rm .nano_history??

---

### Post by g8m on 2007-02-22
Probably, but if you're not sure, why not rename it. So you can restore it if necessary.

---

### Post by Jimcanoa on 2007-02-22
I got the same error, what I did is change the owner of the file from root to me:

```
# sudo chown 'youruser':'yourgroup' .nano_history
```

Hope it works.

---

### Post by Maelgwyn on 2007-02-22
All sorted :)

I just renamed it to .nano_history_backup and now it works fine :)

---

