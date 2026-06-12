---
title: "Script thath changes icon"
date: 2007-12-23
forum: General Help
---

### Post by romyr on 2007-12-23
How can I write a bash script that changes an icon of a link placed on desktop ?
Same as RightClick/Properties/Symbol or eventually RightClick/Properties/Notes

Many thanks.

---

### Post by PeterJS on 2007-12-23
The change isn't immediate, it takes about 30 second to update, but take a look at:
```

#!/bin/bash

PREFIX="$HOME/Desktop"
ITEM="$PREFIX/something.desktop"
FINAL_ICON="/some/path/to/an/icon.png"

sed -i "s|\(Icon.*\)=.*|\1=$FINAL_ICON|g" $ITEM

```

The use of pipes as seperators is non-standard / is usally used, but since final icon contains a path with /'s in a another seperator needed to be used.

---

### Post by romyr on 2007-12-23
Many thanks.
I' ll go to try; for me is diffucult to understand the "sed" invocation.

Please, can give me a link or explain  how an icon is associated to an object.

---

### Post by PeterJS on 2007-12-23
To understand the desktop item format just cat one of them, things are pretty clearly named.

In this case the two that we are interested are Icon and Icon[Locale]. The -i tells sed that we're going to be working in place, writing back to where we read from. Now lets dissect the monstrosity of a sed statement up there:
```

"s|\(Icon.*\)=.*|\1=$FINAL_ICON|g"

```The "s|" is just how you start a sed command off, it most case it would be "s/" instead, but as I said before I'm using an different separator to allow for an absolute path. The "\(" is the beginning of a capture sequence, the way a capture sequence works is that is stores everything in it for late printing, the "\)" ends the sequence. So what are we capturing the "Icon.*", which is the literal letters I-c-o-n followed by any number (including 0) of wild card characters. This allows our capture sequence to match both Icon and Icon[Locale]. The "=.*" matches a literal = and then everything to the end of the line, but since it's outside of a capture sequence it won't be saved. The "|" denotes the break between the read and write sections. The first thing in the write section is \1 which tells sed to write the first thing it captured, which in this case will be either Icon or Icon[Locale], and then a literal = and the path to the icon is inserted as a BASH variable substitution. Lastly the "|g" tells sed the scope it's operating on, g is for global, so it will replace every thing that matches.

And the $FILE after that whole mess tells it which file to read and write.

General Regex
[http://www.regular-expressions.info/](http://www.regular-expressions.info/)
Capture specific stuff
[http://developer.apple.com/documentation/OpenSource/Conceptual/ShellScripting/RegularExpressionsUnfettered/chapter_6_section_7.html](http://developer.apple.com/documentation/OpenSource/Conceptual/ShellScripting/RegularExpressionsUnfettered/chapter_6_section_7.html)

---

### Post by romyr on 2007-12-23
Thank you for the exhaustive explanation but, perhaps i was not clear enough.
I have made a hardlink of my script.

ln     /usr/share/my_script      /home/my_session/Desktop

I want to change its icon.

If I cat it I get the list of the script itself but I dont see any "Icon" keyword.
The only way I have found to manage its icon is interactively thru RightClick and so on.

Where I can found the key  "Icon" ?

Thanks again

---

### Post by PeterJS on 2007-12-23
> **romyr said:**
> Thank you for the exhaustive explanation but, perhaps i was not clear enough.
I have made a hardlink of my script.

ln     /usr/share/my_script      /home/my_session/Desktop


Ah, you don't get there from here, since it's a hard link to the actual file for all intents and purposes it is the file it self. So the icon it has right now is the default Icon for shell scripts, you could change your icon theme, but that would change the icon for all scripts everywhere. (Assuming you're running Gnome here) I would unlink the script, right click on the desktop, select create launcher... and then for the command put in the name of your script. This will create a .desktop file (a lot like a windows shortcut), here's one of the ones I was using last night to test that monster sed statement:
```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=konqueror
Name[en_US]=Nautilus
Exec=nautilus
Comment[en_US]=Phase2
Name=Nautilus
Comment=Phase2
Icon=konqueror

```

---

### Post by romyr on 2007-12-23
Perfect !
It works fine and I have perfectly understund both use of "sed" and management of .desktop files.
You, not sed, are a monster.

Many, many thanks.

---

