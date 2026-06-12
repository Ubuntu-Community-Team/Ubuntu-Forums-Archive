---
title: "Search within files"
date: 2007-06-23
forum: General Help
---

### Post by EdUbun on 2007-06-23
Hello. I need to search within files for I'm missing something in a configuration an I have no clue which file in the webdirectory.

So in the root of the web directory I type "fgrep -l -n -R "ThemeXP"" only to see nothing happen. There comes no prompt and no status.

How to do this?

---

### Post by eggdeng on 2007-06-23
Try ```
fgrep -lnR ThemeXP /var/www
``` assuming /var/www is your web root directory. although```
 grep -R ThemeXP /var/www
```would probably be more like what you want.

---

### Post by EdUbun on 2007-06-24
Thanks!!
Now I can continue my search where I missed something.

---

### Post by phyrewall on 2008-01-21
In Gutsy, simply go to the "Places" menu, then select "Search for Files...". This will bring up a GUI that allows you to select where you want to search, and includes options to search within files, certain date ranges, even other file systems.

Hope that helps!

---

