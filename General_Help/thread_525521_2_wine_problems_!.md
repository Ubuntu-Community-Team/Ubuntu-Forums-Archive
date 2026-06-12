---
title: "2 wine problems ?!"
date: 2007-08-14
forum: General Help
---

### Post by doh224 on 2007-08-14
hi all..

I have 2 problems with wine:

first:

when I play diablo 2 or CSS it shows my panels in the top and in the bottom of the screen? (look at this to see what I mean:  file:///home/akaran234/Desktop/Sk%C3%A6rmbillede-Diablo%20II.png
it only shows the bottom panel, but there is one at the top also!

second: 
I tried to install winetools, and everything seemed to work out pretty well, but when I type "wt" to open winetool the terminal says: 

akaran234@akaran234-desktop:~/Desktop/winetools-0.9jo-III$ wt
detecting Wine version... done.
Drive C: is /home/akaran234/.wine/drive_c
Wine 0
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0".
akaran234@akaran234-desktop:~/Desktop/winetools-0.9jo-III$

And it pops up with an error that says: "winetools cannot run with a wine version older than 20050628..."
and my wine version is up to date?

can someone help me with these problems? thanks for any help given...

-doh

---

### Post by doh224 on 2007-08-14
ups my link didn't work... hope you understand anyway

---

### Post by Kralizec on 2007-08-14
To solve the second problem, instead of executing 'wt', execute:

```

WINEVER=0.9 wt

```
This should solve the problem. About your first problem, I cannot help. You may get more help on a wine forum than here though, if no solutions come up.

---

### Post by doh224 on 2007-08-14
> **Kralizec said:**
> To solve the second problem, instead of executing 'wt', execute:

```

WINEVER=0.9 wt

```
This should solve the problem. About your first problem, I cannot help. You may get more help on a wine forum than here though, if no solutions come up.

hey thanks... it works now :) 

then there is only one unanswered question...

---

