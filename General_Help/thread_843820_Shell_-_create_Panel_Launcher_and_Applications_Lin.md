---
title: "Shell - create Panel Launcher and Applications Link"
date: 2008-06-28
forum: General Help
---

### Post by iwarner on 2008-06-28
Hi

I am trying to create an application launcher and Link for Eclipse.

I basically download eclipse and untar and then want to create the links all in one shell script.

I have so far for the applications link - however this gives me a permissions denied - maybe cause its in the usr folder, but I have no idea really?

```

sudo echo -e "
[Desktop Entry]
Encoding=UTF-8
Type=Application
Terminal=false
Icon="/media/DATA/02. Applications/Eclipse/icon.xpm"
Exec="/media/DATA/02. Applications/Eclipse/eclipse"
Name=Eclipse
" >> eclipse.desktop

```

any help appreciated on this please, I havent even got round to creating the panel link.

---

### Post by sisco311 on 2008-06-28
try:
```
echo -e "
[Desktop Entry]
Encoding=UTF-8
Type=Application
Terminal=false
Icon="/media/DATA/02. Applications/Eclipse/icon.xpm"
Exec="/media/DATA/02. Applications/Eclipse/eclipse"
Name=Eclipse
" | sudo tee -a  eclipse.desktop

```

---

### Post by iwarner on 2008-06-28
I still get:

/media/DATA/02. Ubuntu Setup/Eclipse: line 46: sudo: Permission denied

thanks

---

### Post by sneakyimp on 2011-07-04
I'm trying to accomplish the same thing here but don't really understand these commands being used.  Sorry for crashing your thread but can anyone clue me in?

---

### Post by wildmanne39 on 2011-07-05
> **sneakyimp said:**
> I'm trying to accomplish the same thing here but don't really understand these commands being used.  Sorry for crashing your thread but can anyone clue me in?Hi, click on the power users guide in my signature below this text and it tells you how to create launchers for natty.

---

### Post by sneakyimp on 2011-07-05
thanks!

---

### Post by wildmanne39 on 2011-07-05
> **sneakyimp said:**
> thanks!
Hi, your welcome.

---

