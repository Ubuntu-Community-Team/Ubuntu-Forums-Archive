---
title: "Image resize script help"
date: 2006-09-04
forum: General Help
---

### Post by _simon_ on 2006-09-04
```

#! /bin/sh

# Dialog box to choose thumb's size
SIZE=`zenity --list --title="Choose the thumbnail's size" --radiolist --column="Check" --column="Size" "" "320x240" "" "640x480" "" "800x600" "" "1024x768" "" "1280x1024"`

if [ "${SIZE}" == "" ]; then    
zenity --error --text="Size not defined by user.
Please choose a size to use. "
exit 1
fi

# How many files to make the progress bar
PROGRESS=0
NUMBER_OF_FILES=`find -iname "*.jpg" -maxdepth 1 | wc -l`
let "INCREMENT=100/$NUMBER_OF_FILES"

mkdir -p Resized

# Creating thumbnails. Specific work on picture should be add there as convert's option
(for i in *.jpg *.JPG; do
echo "$PROGRESS";
echo "# Resizing $i";
convert -resize "${SIZE}"  -bordercolor black -border 10x10 -quality 50 "${i}" Resized/"${i}"
let "PROGRESS+=$INCREMENT"
done
) | zenity  --progress --title "$Creating thumbnails..." --percentage=0

```

I found this in a very old thread. Can anyone tell me why the 1280x1024 doesn't actually work? I tried it on a 1600x1200 image and it resized it to 1300x980

From what I have read it needs an ! after the size but no matter where I add it, it doesn't work.

---

### Post by yopnono on 2006-09-04
Don't know. 
But you can use gimp and plugins to resize img, or use the gthumb.

Gimp plugins:
[http://registry.gimp.org/index.jsp](http://registry.gimp.org/index.jsp)

---

### Post by _simon_ on 2006-09-04
I need it for batch resizing though. Can't find a gimp plugin that does that.

---

### Post by blackened on 2006-09-04
You're right about the ! needed. Because 1280x1024 doesn't preserve the 4:3 aspect ratio it requires the ! after 1280x1024.

The easiest way to do this is on the line just before the convert command check if the user selected 1280x1024, then alter the variable value accordingly:

```
if [ "${SIZE}" == "1280x1024" ]; then
SIZE="1280x1024!"
fi
```

then commence with the convert.

Also some checking for capitalization in the file extension is required. Right now it's throwing an error at the end of the script.

---

### Post by yopnono on 2006-09-04
> **_simon_ said:**
> I need it for batch resizing though. Can't find a gimp plugin that does that.

There is plugin for gimp, just for that (batch resize). Don't remember the name of it. Anyhow you can use gthumb and select all img and resize.

---

### Post by _simon_ on 2006-09-04
> **yopnono said:**
> There is plugin for gimp, just for that (batch resize). Don't remember the name of it. Anyhow you can use gthumb and select all img and resize.

Didn't realise gthumb could do it!

Just found and modified a script that can be used from nautilus:

```

#!/bin/bash

# Resize selected image files.

size=`zenity --entry \
             --title "Resize Image" \
             --text "Resize to (pixels)"`

if [ $size = "" ]; then
	exit 0
fi

mkdir -p Resized

for arg; do
	convert -size "${size}x${size}" -resize "${size}x${size}!" "$arg" Resized/"$size-$arg"
done

```

---

### Post by f76 on 2007-06-26
the gthumb batch resize rocks!

---

### Post by megamania on 2007-06-26
> **f76 said:**
> the gthumb batch resize rocks!
there's also a program currently in beta testing, phatch. it looks promising.

there's a thread in the forums, just search for "phatch".

---

### Post by stani on 2007-06-30
> **megamania said:**
> there's also a program currently in beta testing, phatch. it looks promising.

there's a thread in the forums, just search for "phatch".

Yes Phatch will do all this for you with a user friendly interface (no command line). You can get a deb installer if you want, see more here:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

---

