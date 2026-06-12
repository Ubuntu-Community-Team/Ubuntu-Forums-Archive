---
title: "Zip files with no extension"
date: 2019-04-04
forum: General Help
---

### Post by raleigh3 on 2019-04-04
I want to zip files with no extension, in particular a file named On_Resume

This does not work.

```
zip -u Ubuntu_Documents.zip *.txt *.doc *.rtf *.html *.png *.pdf *.odt *.ods *.odg *.csv *.png *.xls On_Resume*
```

---

### Post by oldos2er on 2019-04-04
Please post the full output of the command; simply telling people it doesn't work doesn't convey any information.

---

### Post by spjackson on 2019-04-04
What's the "?" doing there? Remove it.

---

### Post by #&amp;thj^% on 2019-04-04
I'm not sure if this is what you want but, Alternatively, zip also has a -r (recursive) option to do entire directory trees at once (and not have to worry about the dotfile problem):
```

zip -r myfiles.zip mydir
```

**where <mydir> is the directory containing your files**. Note that the produced zip will contain the directory structure as well as the files.
In some case's you will have to start in directory higher than the target, example below;
```
zip -r myfiles.zip /home/me

```
You'll see that it was started in /home not /me

---

### Post by raleigh3 on 2019-04-04
> **oldos2er said:**
> Please post the full output of the command; simply telling people it doesn't work doesn't convey any information.

```
andy@7_~/Downloads$ Backup_18_04.sh

Backing up Hard Drive.
	zip warning: name not matched: *.rtf
	zip warning: name not matched: *.ods
	zip warning: name not matched: *.odg
	zip warning: name not matched: *.csv
	zip warning: name not matched: On_Resume

```

---

### Post by raleigh3 on 2019-04-04
> **spjackson said:**
> What's the "?" doing there? Remove it.

No change.

---

### Post by raleigh3 on 2019-04-04
This works.

```
tar -cvzf output.tar.gz *.sh *.txt *.c On_Resume
```

---

