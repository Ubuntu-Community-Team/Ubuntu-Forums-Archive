---
title: "File Renamer Like NameWiz"
date: 2005-06-28
forum: General Help
---

### Post by antilog on 2005-06-28
Is there a handy GUI mass file renamer for Ubuntu like NameWiz for PC?

Thanks

---

### Post by jiyuu0 on 2005-06-28
[QUOTE=antilog]Is there a handy GUI mass file renamer for Ubuntu like NameWiz for PC?

Thanks[/QUOTE]

i use this to rename mass image files...

this prog is command base though:
[http://ubuntuguide.org/#mvb](http://ubuntuguide.org/#mvb)

---

### Post by ow50 on 2005-06-29
You can try [purrr](http://mathrick.org/software/purrr.html).

Or, for simple renamings a nautilus-script:
```
#!/bin/bash

# Rename selected files with rename.

search=`zenity	--entry \
				--title "Rename" \
				--text "Search for (Perl regular expression)"`
replace=`zenity	--entry \
				--title "Rename" \
				--text "Replace with (Perl regular expression)"`

for i in $*; do
	rename "s/$search/$replace/g" "$i"
done
```

---

### Post by Efros on 2007-02-16
[Flash Renamer]("http://www.rlvision.com/flashren/about.asp") will run under wine, you just have to get a hold of [msvbvm60.dll]("http://www.dll-files.com/dllindex/dll-files.shtml?msvbvm60") and put it in it Program Files directory.

---

### Post by Marsolin on 2007-02-17
[KRename]("http://linuxappfinder.com/package/krename") and [GwenRename]("http://linuxappfinder.com/package/gwenrename") are two graphical options.

---

### Post by aysiu on 2007-02-17
I'm a big fan of KRename.

---

