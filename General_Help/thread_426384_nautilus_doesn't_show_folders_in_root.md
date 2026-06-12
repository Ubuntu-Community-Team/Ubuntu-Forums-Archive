---
title: "nautilus doesn't show folders in root"
date: 2007-04-28
forum: General Help
---

### Post by jokr004 on 2007-04-28
for some reason, nautilus will only show three folders in the root directory, 'debian' 'home' and 'media'.  I can still navigate to the now hidden directories by typing in the location and thunar can see them, same with just an ls in a terminal.  Does anyone know what could have caused this?

---

### Post by Patrick K on 2007-04-28
In preferences there is a check box to show hidden and backup files. Give it a shot, just might do waht you want. 

You can also hit CTRL-h

---

### Post by chrisccoulson on 2007-04-28
You will also find a file called '.hidden' in the root folder, which contains a list of the folders to hide. If you want to unhide them permanently, then delete this file.

---

### Post by jokr004 on 2007-04-28
thank you, I removed them from .hidden and it works

---

### Post by fragos on 2007-04-28
> **chrisccoulson said:**
> You will also find a file called '.hidden' in the root folder, which contains a list of the folders to hide. If you want to unhide them permanently, then delete this file.

I was curious about this ".hidden" file so I looked for mine and found it doesn't exist in /root or my /home.  Where might it have come from and how is it's purpose different from place "." in front of a file name?

---

### Post by elephant007 on 2007-04-28
> **chrisccoulson said:**
> You will also find a file called '.hidden' in the root folder, which contains a list of the folders to hide. If you want to unhide them permanently, then delete this file.

Sweet tip!

---

