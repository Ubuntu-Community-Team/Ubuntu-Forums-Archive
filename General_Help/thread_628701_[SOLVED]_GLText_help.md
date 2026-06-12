---
title: "[SOLVED] GLText help"
date: 2007-12-01
forum: General Help
---

### Post by solwyn on 2007-12-01
Does anyone know how to change the text on the GLText screensaver?

---

### Post by -grubby on 2007-12-01
I don't believe there is a way to change it (which is sad)
EDIT: I stand corrected. But I still think it should be easier to change

---

### Post by idar on 2007-12-03
> **solwyn said:**
> Does anyone know how to change the text on the GLText screensaver?

In the following file /usr/share/applications/screensavers/gltext.desktop
change the line
Exec=gltext -root
into 
Exec=gltext -root -text 'your text'

see also gltext man page.

---

### Post by dimbulb1024 on 2007-12-03
FYI: by trial and error I found your text needs to be in these " not ' -  so it should read:
Exec=gltext -root -text "your text"

---

### Post by solwyn on 2007-12-03
When I click Save to save the change, I get a notice that I do not have permissions necessary to change the file.  Now what?

---

### Post by dimbulb1024 on 2007-12-04
You need to open gedit with root permissions to be able edit the file. So in Terminal type
```
sudo gedit
```
Then navigate to the file and you will be able to save your edits.

---

### Post by solwyn on 2007-12-04
It worked.  Thanks everyone for all your help!

---

