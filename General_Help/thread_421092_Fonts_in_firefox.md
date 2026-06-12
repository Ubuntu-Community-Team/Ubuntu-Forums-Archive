---
title: "Fonts in firefox"
date: 2007-04-24
forum: General Help
---

### Post by MiCovran on 2007-04-24
I just installed 'Macromedia Flash plugin' and 'Ubuntu restricted extras' from Add/Remove. I then realized I don't need Ubuntu restricted extras so I removed them.

But now all fonts in firefox are diferent! I don't like them this way. Is there a way to get them back the way they were? (only fonts in web pages are changed, not in Firefox's GUI)

So, can anyone help, please?
Thanks.

---

### Post by bwhite82 on 2007-04-24
Edit > Preferences > Content Tab

---

### Post by MiCovran on 2007-04-24
OK, now could you please send me what font is your 'Default font' and what are your 'Advanced fonts' (including font size). I just can't get it as it was.

---

### Post by bwhite82 on 2007-04-24
Default: serif size: 16
Advanced:
serif          16
serif
sans-serif
monospace   12

---

### Post by kc8hr on 2007-04-24
> **MiCovran said:**
> I just installed 'Macromedia Flash plugin' and 'Ubuntu restricted extras' from Add/Remove. I then realized I don't need Ubuntu restricted extras so I removed them.

But now all fonts in firefox are diferent! I don't like them this way. Is there a way to get them back the way they were? (only fonts in web pages are changed, not in Firefox's GUI)

So, can anyone help, please?
Thanks.

Try backing up your bookmarks and passwords, then just delete your ~/.mozilla config directory. Then start Firefox--it will rebuild the directory with the default fonts. Then you can import your bookmarks and passwords.

Good luck!
Tim

---

### Post by strabes on 2007-04-24
sudo aptitude install msttcorefonts

msttcorefonts is a package that is included with ubuntu-restricted-extras

---

### Post by MiCovran on 2007-04-24
> **strabes said:**
> sudo aptitude install msttcorefonts

msttcorefonts is a package that is included with ubuntu-restricted-extras
Thanks a lot for the info. I just removed that msttcorefonts package and everything went back to normal.

---

