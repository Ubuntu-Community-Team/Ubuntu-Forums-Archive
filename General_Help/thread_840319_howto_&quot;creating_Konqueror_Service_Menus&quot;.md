---
title: "howto &quot;creating Konqueror Service Menus&quot; ?"
date: 2008-06-25
forum: General Help
---

### Post by taisao on 2008-06-25
Hi,

I'm trying to create a service menu out of this command
```
find . -iname "Thumbs.db" -execdir rm {} \; && find . -iname "Desktop.ini" -execdir rm {} \;
```

At [http://developer.kde.org/documentation/tutorials/dot/servicemenus.html](http://developer.kde.org/documentation/tutorials/dot/servicemenus.html) they say this > If you have a complex task that requires more than one command (for example if we wanted to copy the image file somewhere first and then use dcop to set it as the background) use a shell:

Exec=/bin/sh -c "<YOUR COMMANDS HERE>"

but I didn't manage to get it to work, please guide me :confused:

--
This is what I have, the first 2 work, but the last one not
```
Desktop Entry]
ServiceTypes=inode/directory
Actions=Remove_Desktop.ini;Remove_Thumbs.db;Remove_Windows_files;
Encoding=UTF-8

[Desktop Action Remove_Desktop.ini]
Name=Remove Desktop ini files!
Icon=
Exec=find %U -iname "Desktop.ini" -execdir rm {} \;

[Desktop Action Remove_Thumbs.db]
Name=Remove Thumbs db files!
Icon=
Exec=find %U -iname "Thumbs.db" -execdir rm {} \;

[Desktop Action Remove_Windows_files]
Name=Remove windows files!
Icon=
Exec=/bin/sh -c "find %U -iname "Thumbs.db" -execdir rm {} \; && find %U -iname "Desktop.ini" -execdir rm {} \;"

```

---

### Post by editrix on 2008-06-25
I found a really good tutorial for this on the web:

[http://developer.kde.org/documentation/tutorials/dot/servicemenus.html](http://developer.kde.org/documentation/tutorials/dot/servicemenus.html)

---

