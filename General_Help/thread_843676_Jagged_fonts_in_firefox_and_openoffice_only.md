---
title: "Jagged fonts in firefox and openoffice only"
date: 2008-06-28
forum: General Help
---

### Post by Mr Gav on 2008-06-28
I'm running Xubuntu 8.04 and all my fonts look fantastic apart from in firefox and openoffice. To remedy this as soon as I have logged in I have to go to Settings Manager/User Interface and untick anti-aliasing and then re-tick it. Then when I open firefox or openoffice their fonts look splendid too!?

Boths apps will also randomly lose their smoothness during a session and I will have to go through the workaround to get them looking good again. The fonts in everything else always look great.

Does anyone know why this might happen and if there is anything I can do so I don't have to manually re-set the anti-aliasing just after logon.

thanks

g

---

### Post by cpetercarter on 2008-06-28
Forgive me if you know this already, but you could try altering the default font in Firefox, to see if it makes a difference.

Edit > Preferences > Content

Generally, a sans-serif font looks best on a web page.

---

### Post by Mr Gav on 2008-06-28
It's not just the webpage fonts that look bad but the menus address and search fields as well. Its as if anti-aliasing has not been turned on for these apps for some reason.

---

### Post by dizee on 2008-06-28
hi Mr Gav. OpenOffice fonts have never antialiased properly for me neither. As for the firefox issue, I had exactly the same problem. Firefox alone ignored my antialiasing settings unless I re-applied them. Deleting the ~/.gtkrc-2.0 file seemed to work for my Xfce session, but the problem remains in Openbox. Worth a shot anyway.

---

### Post by Mr Gav on 2008-06-29
thanks for the pointer dizee. i may be being daft however but i can't find the ~/.gtkrc-2.0 file. btw i never get this issue in ubuntu so must be an xfce issue.

looked in home folder whilst showing hidden files

---

