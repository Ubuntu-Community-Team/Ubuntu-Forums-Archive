---
title: "copy command help"
date: 2006-12-19
forum: General Help
---

### Post by sertmann on 2006-12-19
Hey

Wondering if anyone could help me come up with a command to do this, been googleing around for it - but no luck...

Got alot of music folders, with albumart saved in jpg - I want to rename all of these to "folder.jpg", thought this 

cp -R *.jpg folder.jpg 

would do the trick, but apparently not - anyone who can figure out a way?

- Stefan

---

### Post by taurus on 2006-12-19
Is folder.jpg a directory/folder or a file?  If you don't already have folder.jpg (directory), then it will try to copy everything, *.jpg, to file folder.jpg which it can't...

---

### Post by hal10000 on 2006-12-19
I suppose in any subdirectory there is only **one** .jpg file with an arbitrary name and you want to rename these jpg to a jpg-file called folder.jpg in the same directory.
If so, then you can try the following:
```

find /your/music/dir/ -name "*.jpg" -execdir mv {} folder.jpg  \;

```
But be careful, if there is more than one jpg file in a subdirectory, only one file will be renamed and the other will be removed!!!

---

