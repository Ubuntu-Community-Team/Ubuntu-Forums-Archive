---
title: "Debian Menu!"
date: 2006-12-21
forum: General Help
---

### Post by Valinski on 2006-12-21
This may be a stupid question but i cant seem to find the package that installs the Debian menu section under the applications menu so i can see a list of my installed programs. 

What is the package called? 

Thanks!

---

### Post by riven0 on 2006-12-21
> **Valinski said:**
> This may be a stupid question but i cant seem to find the package that installs the Debian menu section under the applications menu so i can see a list of my installed programs. 

What is the package called? 

Thanks!

If you go to System >> Preferences >> Menu Layout it should give you the option to add in the Debian menu.

---

### Post by lamego on 2006-12-21
I believe its called "menu".
lamego@lamego-desktop:/var/lib/dpkg/info$ apt-cache show menu
...
Description: generates programs menu for all menu-aware applications
 Debian menu keeps transparently the menus in the different
 window-managers in sync with the list of installed programs.
...

---

### Post by Valinski on 2006-12-21
I looked in the preferences as you suggested. The Debian box was already ticked! :(  Just trying the other suggestion now! 

Thanks for your help.

---

### Post by Valinski on 2006-12-21
Ive got it working from that line of code. Thank you lamego. Its visible now

---

### Post by lamego on 2006-12-21
Next time you can search for it, from the terminal:
```
apt-cache search debian menu
```
Sometimes it does find what you need ;)

---

### Post by Valinski on 2006-12-21
Ok thanks i'll write it down!

---

