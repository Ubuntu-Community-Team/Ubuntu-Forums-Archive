---
title: "Zip file structure invalid"
date: 2020-04-17
forum: General Help
---

### Post by raleigh3 on 2020-04-17
This used to work?

zip  Ubuntu_Scripts.zip *.sh *.rb *.c *.py *.txt On_Resume*
	zip warning: missing end signature--probably not a zip file (did you
	zip warning: remember to use binary mode when you transferred it?)
	zip warning: (if you are trying to read a damaged archive try -F)

zip error: Zip file structure invalid (Ubuntu_Scripts.zip)

---

### Post by TheFu on 2020-04-17
I'd think it still should work.  Some odd guesses.
[LIST]
[*]Out of storage anywhere on the machine, perhaps / or /var/?
[*]Corrupted files?  Check them each.
[*]Some sort of snap package for zip that cannot access the CWD?  Snaps are picky about where they can read files from.
[/LIST]

Doubt any of those are it, but you never know.

Have you tried forcing the zip package to be reinstalled?

Any reason to use zip over tgz?  Neither are really great for backups, but if you just want to move some files between systems quick and the systems aren't networked (use rsync ) and not larger than 50MB total, then something like

```
$ tar zcvf Ubuntu_Scripts.tgz  *.sh *.rb *.c *.py *.txt On_Resume*
```
would get the stuff. Heck, I'd make that into a gmake Makefile target.

---

### Post by raleigh3 on 2020-04-17
I had a zero byte zip file.

After I deleted it, the zip command starting working again. ???

I had similar zip commands for other files that were working, so I knew zip was not corrupted.

---

