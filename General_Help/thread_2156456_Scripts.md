---
title: "Scripts"
date: 2013-06-21
forum: General Help
---

### Post by GR8YFOX on 2013-06-21
Hello.

I have a couple of scripts that I want to use but I would like for them to be tweaked more before I can use them.  What I would like to happen is for progress to be displayed after selecting to where the file(s)/folder(s) will be going to and to remember the last used location/folder.

**Copy To Script**
```
#!/bin/bash

FILE=`echo -n $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS`

DESTINO=$(zenity --title "Select a folder to move" --file-selection --directory)
cp -uR "$FILE" "$DESTINO"
exit
```

**Move To Script**
```
#!/bin/bash

FILE=`echo -n $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS`

DESTINO=$(zenity --title $FILE --file-selection --directory)

#sed 's# #\ #g' $DESTINO

mv -u "$FILE" "$DESTINO"
exit
```

If these scripts are incorrect, then please can they be corrected to its intended outcome and the two requests that I mentioned be added too.

Thank you.

:D

---

### Post by HiImTye on 2013-06-21
use```
rsync -LPau
``` to get progress, you may need to install rsync ```
sudo apt-get install rsync
```for move add```
--remove-source-files
```
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by GR8YFOX on 2013-06-22
I already have rsync installed.  Where do I add those two commands and in which script?

---

### Post by prodigy_ on 2013-06-22
You can use rsync instead of cp/mv. Another possible alternative is **cpio --passthrough --dot** (see [cpio manual](http://www.gnu.org/software/cpio/manual/cpio.html) for more info).

Also you don't want to use uppercase names for your variables (such as $FILE). Uppercase names are often reserved for system or shell variables. Use lowercase instead.

---

