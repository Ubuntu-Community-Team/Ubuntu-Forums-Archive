---
title: "Nautilus Script help?"
date: 2007-01-23
forum: General Help
---

### Post by theaverageidiot on 2007-01-23
I want to make a nautilus script that simply does this: When I right click a file and choose the nautilus script, it opens a terminal and outputs the filename.

Thanks! :)

---

### Post by renzokuken on 2007-01-23
have you got the package "nautilus-scripts" installed, its in Automatix.

this package allows to create custom scripts for nautilus with a GUI interface

---

### Post by ardchoille42 on 2007-01-23
It sounds to me like you are trying to learn how to make your own nautilus scripts. Here are some scripts that may help you:

**File Name** - outputs the file name
```

#!/bin/sh

for arg
do
 
  gdialog --title "File Name" --msgbox "File name: $arg" 200 200

done


```

**File Type** - outputs the file type
```

#!/bin/sh

for arg
do
 
filetype=$(file "$arg")

  gdialog --title "File Type Detection" --msgbox "File $filetype" 200 200

done


```

**Mime Type** - outputs the mime type
```

#!/bin/sh

for arg
do
 
filetype=$(file -i "$arg")

  gdialog --title "Mime Type Detection" --msgbox "File $filetype" 200 200

done

```

**Copy To** - copies a files, or files, to a user specified location
```

#!/bin/bash
location=`zenity --file-selection --directory --title="Select a directory"`
for arg
do
if [ -e "$location"/"$arg" ];then
   zenity --question --title="Conflict While Copying" --text="File "$location"/"$arg" already exists. Would you like to replace it?"
   case "$?" in
      1  )  exit 1 ;;
      0  )  cp -R "$arg" "$location" ;;
   esac
else
   cp -R "$arg" "$location"
fi
done


```

**Move To** - moves a files, or files, to a user specified location
```

#!/bin/bash
location=`zenity --file-selection --directory --title="Select a directory"`
for arg
do
if [ -e "$location"/"$arg" ];then
   zenity --question --title="Conflict While Moving" --text="File "$location"/"$arg" already exists. Would you like to replace it?"
   case "$?" in
      1  )  exit 1 ;;
      0  )  mv "$arg" "$location" ;;
   esac
else
   mv "$arg" "$location"
fi
done


```

**Open With Gedit** - opens a file with gedit
```

#!/bin/bash
for arg 
do
  exec gedit "$arg" &
done 


```

**Open With [COLOR="Red"]GKSU[/COLOR] Gedit** - opens a file in gedit with [COLOR="Red"]admin rights[/COLOR]
```

#!/bin/bash
for arg 
do
  exec gksu -g gedit "$arg" &
done 


```

There's a nice big collection of nautilus scripts [here]("http://g-scripts.sourceforge.net/"). Nautilus scripts are cool and are a great way to extend the functionality of Nautilus :)

---

