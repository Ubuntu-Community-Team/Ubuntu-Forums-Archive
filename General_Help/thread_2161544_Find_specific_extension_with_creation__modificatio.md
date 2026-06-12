---
title: "Find specific extension with creation / modification date"
date: 2013-07-11
forum: General Help
---

### Post by alfirdaous on 2013-07-11
Hello everybody,

I al wonderring if we can find a file name (file.sql) or any sql file with creation / modification date on 2013?

thx in advance

---

### Post by sudodus on 2013-07-11
You can use something like this (-200 means during the last 200 days). It should print all sql files in and below the current directory (dot) created during the selected period of time along with the date.

```
sudo find . -name "*.sql" -mtime -200 -printf "%p %c \n"
```

See ```
man find
``` for details.

So change directory to where you want to search and run the command. If you want to search the whole root partition,

```
cd /
``` and run the command.

---

### Post by alfirdaous on 2013-07-11
Oh thanks, I used mtime, I am looking for a specific date, i.e: 2013

---

### Post by steeldriver on 2013-07-11
You can create date ranges in find with *-newermt <startdate> -a ! -newermt <enddate>* ("mtime newer than startdate and not newer that enddate") e.g.

```
find . -newermt '01 Jan 2013' -a ! -newermt '01 Jan 2014'
```

---

### Post by alfirdaous on 2013-07-12
That's look good, so we can do like this:

```

$ sudo find . -iname ".sql" -newermt '01 Jan 2013' -a ! -iname ".sql" -newermt '01 Jan 2014'

```

---

### Post by steeldriver on 2013-07-12
You need a glob (wildcard) for the name match and you DON'T need to repeat that part (in fact it won't work the way you wrote it because it will apply the NOT operator to the second iname match). Also it's better to use single quotes to prevent the shell expanding the glob before passing it to find.

```
sudo find . -iname [COLOR=#0000ff]'*[/COLOR].sql[COLOR=#0000ff]'[/COLOR] -newermt '01 Jan 2013' -a ! -newermt '01 Jan 2014'
```

The -a is actually not essential since AND is the default logic for 'find' tests (I just find it easier to remember that way) - fwiw I'd probably put the date matches first

```
sudo find .  -newermt '01 Jan 2013' ! -newermt '01 Jan 2014 -iname '*.sql'
```

---

### Post by alfirdaous on 2013-07-12
we use -type f for files and how about folders?

---

### Post by steeldriver on 2013-07-12
Folders (directories) are *-type d* and symbolic links are *-type l* (ell)

The man page is a lot to take in but is actually quite useful if you just skip down to the 'TESTS' section

```
man find
```

Obviously you only need sudo if you're trying to search directories that your regular user doesn't have permissions in

---

