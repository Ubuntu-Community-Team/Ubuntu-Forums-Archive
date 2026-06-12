---
title: "Adding ISO8859-1 locale to 14.04 LTS"
date: 2016-01-07
forum: General Help
---

### Post by marcgrdn on 2016-01-07
Hi guys

Haven't posted on this forum in years but it has been such a source of help in the past I thought I would give it a shot again with an issue I've recently experienced.

I have some older files that unfortunately are using en_ISO8859-1 encoding. In past versions of Ubuntu I would just add the en_ISO8859-1 encoding locales to the system and it would happily use one or the other.

Unfortunately in 14.04 LTS I now no longer see ISO8859-1 locales in the list of supported locales when I use the "locale -a" command.

I ran "sudo locale-gen en_ZA.iso88591" in an attempt to get it to generate but I think if it isn't in that list of supported locales it isn't going to help.

I haven't done this in years and I've forgotten where to start. It also looks like the approach has changed somewhat since I last did it.

Anyway if anybody has an idea of how to go about this please let me know. Thanks in advance. :)

---

### Post by marcgrdn on 2016-01-10
Just bumping the thread in hopes of getting a response. Thanks guys.

---

### Post by SeijiSensei on 2016-01-10
One alternative you might consider if we're talking about a limited number of files is converting them to UTF-8 with iconv:
```
iconv -f ISO8859-1 -t UTF-8 -o output.file input.file
```

Use "iconv -l" to see a list of all supported formats.

---

### Post by marcgrdn on 2016-01-11
Converting is not a bad idea. It is something I foolishly hadn't considered. There are a lot of files that need converting though so I'd need a recursive script to run through them all.

The app that processes these files I don't think is encoding specific. I will need to check.

---

### Post by SeijiSensei on 2016-01-11
```

#!/bin/bash

mkdir -p converted

for f in *
do
     iconv -f ISO8859-1 -t UTF-8 -o converted/$f $f
done

```

Run this in the directory where the files reside.

I never knew about iconv until I had to migrate a PostgreSQL database which had some records in ISO8859-1 that didn't appear correctly on newer servers using UTF-8.  Turned out I could just dump the database to text, run it through iconv, and rebuild it.  What a time-saver!

---

### Post by marcgrdn on 2016-01-12
Thanks so much for the help so far. It really looks like converting these files is going to be the answer. I can't believe I hadn't considered this before. It also makes my life so much easier than having to run the 2 encoding systems side by side like I've had to in the past.

Note though that it isn't just one directory containing these files, the directories are nested at varying levels deep.

My bash scripting isn't the best. Would that for loop run through nested directories or would it just process the files immediately in the current directory?

---

### Post by SeijiSensei on 2016-01-12
It's designed to work in one directory.  "ls -R" will recurse through directories, but I can't find a switch to make it list the files with their full paths. Instead you get results like this:
```

./Access Databases:
total 24800
-rwxr--r-- 1 phl phl  561236 Feb  1  2010 Access Instructions for ECDB.pdf
-rwxr--r-- 1 phl phl  917504 Mar 11  2010 Old Programs.accdb

```
rather than
```
Access Databases/Access Instructions for ECDB.pdf
Access Databases/Old Programs.accdb

```
Maybe there's some tricky combination of switches to ls that provide the right output, but I didn't see one with "man ls".

---

