---
title: "How do I add fonts in Ubuntu 8.04?"
date: 2008-05-22
forum: General Help
---

### Post by raulcarreras on 2008-05-22
There is no ¨Fonts folder¨ under Systems-Preferences. ¨Fonts¨ is a tab under Systems-Preferences-Appearances. The ¨Details¨ button takes me to a dead end. There is no way to ¨Go to Fonts¨.
How do I delete and add new fonts to Ubuntu 8.04 Hardy?
Thank you
[email]raulcarreras@yahoo.com[/email]

---

### Post by dedmonds on 2008-05-23
I believe you can add fonts in Hardy by adding the font files to a .fonts directory in your home directory (e.g., /home/dedmonds/.fonts/ or ~/.fonts/). You may have to create the .fonts directory.

---

### Post by DachaArh on 2008-05-23
Yes I did it that way ;)

I just created folder .fonts in home folder and copied fonts there ;)

---

### Post by jethro10 on 2008-05-23
> **DachaArh said:**
> Yes I did it that way ;)

I just created folder .fonts in home folder and copied fonts there ;)

It may be of no issue to you, but remember that only adds it for the single user.
To add for all users I add them to /usr/share/fonts/truetype for trutype fonts of course.
/use/share/fonts is the root for all fonts.

Jeff

---

### Post by pPrdrm on 2008-05-23
**jethro10** is right. If you want for the new fonts to be system/user wide you have to place them inside the /usr/share/fonts folder. Don't forget to run this command: "**fc-cache -f -v**" to refresh the fonts cashe. I hope it helps.

---

