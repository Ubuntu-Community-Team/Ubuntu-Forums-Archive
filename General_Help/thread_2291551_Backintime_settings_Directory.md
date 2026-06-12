---
title: "Backintime settings Directory"
date: 2015-08-20
forum: General Help
---

### Post by Alistair George on 2015-08-20
Hi does anyone know where profiles are stored as I want to edit my excluded directories manually.  Thanks

---

### Post by howefield on 2015-08-21
Have a look in 

```
~/.config/backintime/config
```

---

### Post by Alistair George on 2015-08-21
> **howefield said:**
> Have a look in 

```
~/.config/backintime/config
```

Thanks but after finding the QT4 version only offers a text file which is not formatted well for bulk exclude of directories.
Each new line has to be prepended which is very different from fwbackups

It would not be so bad if the gui allowed you to drop text directories rather than having to work your way through them all.

---

### Post by Germar on 2015-08-27
> **Alistair George said:**
> Thanks but after finding the QT4 version only offers a text file which is not formatted well for bulk exclude of directories.
Each new line has to be prepended which is very different from fwbackups


You just need to add lines like ```
profile1.snapshots.exclude.X.value=foo
``` where X is a count. When you're done you need to update ```
profile1.snapshots.exclude.size=XX
``` with the number of overall excludes.

> 
It would not be so bad if the gui allowed you to drop text directories rather than having to work your way through them all.

You can drop exclude rules by text in GUI, too. Just press 'Add'

Regards,
Germar, BiT Dev-Team

---

