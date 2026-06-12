---
title: "Recursive deletion in CLI"
date: 2006-10-01
forum: General Help
---

### Post by Nonno Bassotto on 2006-10-01
Even if I've been using Ubuntu for more than a year, I'm a complete newbie at the CLI. I'd like to remove every file named "Thumbs.db" in every subfolder of a given directory. Is there some command to do this?

PS I think I could write a simple script using grep to do the task, but I believe I'm missing something. There should be a simple way to do this with a command in the terminal, but I've not been able to find it.

---

### Post by Miademora on 2006-10-01
untested but something like this should work

```
find /directory | grep Thumbs.db | xargs rm -v
```

---

### Post by Nonno Bassotto on 2006-10-01
Thank you. I didn't know xargs. The command as it stands does not work (it seems there's some problem with spaces) but I will eleborate it.

---

### Post by Nonno Bassotto on 2006-10-01
Should have read better 'find' man page. The command that works is
```

find /Directory -name Thumbs.db -type f -print0 | xargs -0 /bin/rm -f

```

Your code works, but you must add the option -print0 to find and -0 to xargs

---

### Post by PriceChild on 2006-10-01
Wouldn't a simple:
```
rm -R /path/to/start/*/Thumbs.db
```Also work?

---

### Post by Nonno Bassotto on 2006-10-03
I don't know. Can * be used to substitute complicated expressions like /folder1/folder2/ or only parts of a file name?

---

### Post by PriceChild on 2006-10-03
Only one way to find out ;)

---

### Post by hw-tph on 2006-10-06
> **Nonno Bassotto said:**
> Should have read better 'find' man page. The command that works is
```

find /Directory -name Thumbs.db -type f -print0 | xargs -0 /bin/rm -f

```

There is no need to drag xargs into this. find is all you need. You are using three programs (find, xargs and rm) to do something find could do all by itself. This is quicker and cleaner, IMHO.
```
find . -name Thumbs.db -type f -delete
```

Håkan

---

### Post by Nonno Bassotto on 2006-10-06
Thank you, I think this is the cleanest way.

---

