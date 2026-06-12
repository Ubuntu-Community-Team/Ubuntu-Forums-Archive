---
title: "Wine"
date: 2007-09-06
forum: General Help
---

### Post by domat00 on 2007-09-06
what's the command to run wine with Alt + F2, and how can I set it up to be the default program to install windows apps?

---

### Post by domat00 on 2007-09-06
bumpety bump bump.

---

### Post by FuturePilot on 2007-09-07
I think you can right click on an .exe and go to Properties>Opens With
Click Add and go down to the bottom where it says Use Custom Command and type in wine.
You could also start an installer from the terminal like so
```
wine /path/to/executable.exe
```

---

### Post by domat00 on 2007-09-07
Well, that seemed to do the trick, but when I try to execute the file I get an "Unable to elevate, error 2" message.

---

### Post by domat00 on 2007-09-07
bump

---

### Post by Anolis on 2007-11-02
> **domat00 said:**
> Well, that seemed to do the trick, but when I try to execute the file I get an "Unable to elevate, error 2" message.

im having this problem also, when i try to run the xfire installer on my 64bit ubuntu, it runs fine on my 32 bit install however..

---

### Post by falke on 2008-02-20
I got that "unable to elevate , error 2" error when i tried to install EVE Premium.

```
sudo apt-get install winbind
```

fixed it for me =)

---

### Post by falke on 2008-02-21
I have to correct myself.
This error can be avoided by setting the system to "Windows 98" in Wine. :)

---

