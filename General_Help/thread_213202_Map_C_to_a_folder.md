---
title: "Map C:/ to a folder"
date: 2006-07-11
forum: General Help
---

### Post by crazygamer on 2006-07-11
I'm running FileZilla through wine and when it tries to open the temporary files it downloads with gedit, it runs something like: "gedit C:/temp/myfile". Obviously, gedit has no idea what C: is as it's being emulated by wine. Is there any way to map C:/ to a folder so that gedit will know where to go when the path starts with that? Thanks for any help!

---

### Post by Unknowndeepness on 2006-07-11
Should'nt wine do that by itself?

---

### Post by ShiningHolden on 2006-07-11
If your windows partiton is your first partiton then do this:
```

sudo -s
mkdir /windows
mount /dev/hda1 /windows

```

/windows will now be read only, with root only permissions to read. You can access all your files, just not in GUI unless you login as root.

---

### Post by crazygamer on 2006-07-11
Unknowndeepness - I'm not running gedit through wine, so it doesn't know what c: is.

ShiningHolden - I think I didn't explain my problem as well as I should have, sorry. What I need to do is mount /dev/hda1 to "C:" or something of the sort. What I need to happen is if I open up nautilus and type C:/ in the location bar it'll take me to ~/.wine/drive_c/. I'm not sure this is possible, but maybe someone knows how to do this.

---

### Post by nanotube on 2006-07-11
well, easiest way (as i can see), is to make filezilla call not gedit, but a custom script you wrote, that we can call, say, "winegedit" (that's possible to customize in filezilla preferences, i presume)

what the script would do is take the first argument to it, and then substitude C:/ to ~/.wine/drive_c

the script would be pretty simple. 
```
#/bin/bash
gedit `echo "$*" | sed -e 's@C\:/@/home/yourusername/.wine/drive_c/@'`
```
that's all it would take.

place this script somewhere in your path (/usr/local/bin is a good choice), and then set filezilla preferences where your "editor" is "winegedit" rather than just gedit, and watch the magic. :) 

edit: oh and don't forget to chmod the script to be executable ;)

edit2:
haha, well, you could even do one better. just make a link in your home dir to your wine dir, and call it "C:".
```
ln -s ~/.wine/drive_c "C:"
```
all that scripting, for nothing. oops. :)

---

