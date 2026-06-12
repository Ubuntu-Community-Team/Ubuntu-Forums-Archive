---
title: "How do I add /home/username/.local/share to my search path"
date: 2006-08-08
forum: General Help
---

### Post by fubadubrub on 2006-08-08
Hello.  How do I add /home/username/.local/share to my search path.  This share directory has 3 sub-directorys called applications, desktop-directories, mime.  I recently installed Google Earth and it installed and works wonderfully but it was kind enough to let me know about my missing search path.

So how do I add the path.  Thank you.

---

### Post by 5-HT on 2006-08-09
You could add the directory to your PATH in ~/.bashrc.
If GoogleEarth is installed in ~/.local/share/applications, the following should work:
```
 export PATH=$PATH:~/.local/share/applications
``` 

The next time you open a shell, entering *googleearth *should start up the program.

---

### Post by fubadubrub on 2006-08-09
Thank you.  It works.
> **5-HT said:**
> You could add the directory to your PATH in ~/.bashrc.
If GoogleEarth is installed in ~/.local/share/applications, the following should work:
```
 export PATH=$PATH:~/.local/share/applications
``` 

The next time you open a shell, entering *googleearth *should start up the program.

---

