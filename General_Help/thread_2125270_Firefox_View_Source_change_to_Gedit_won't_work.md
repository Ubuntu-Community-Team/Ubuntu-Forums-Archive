---
title: "Firefox View Source change to Gedit won't work"
date: 2013-03-13
forum: General Help
---

### Post by Jameela on 2013-03-13
I have been trying unsuccesfully to change the default 'View Source' in Firefox to Gedit (to edit my web pages)
I'm using Ubuntu 12.04  - please can anyone tell me where I've gone wrong?


I entered   **about:config**   into the Firefox browser address bar, then scrolled down and double clicked -
    **View-Source.editor.external**    to change its status to **True**

Next, I double clicked the line underneath, i.e.    ** View-Source.editor.path **
I entered:  **  usr/bin/gedit **
(found by typing:    **which gedit **   into the Terminal)

Alas: Firefox still does not recognise the change

Please can anyone suggest what is wrong?

---

### Post by stinkeye on 2013-03-13
Did you forget the leading "/" in the path.
eg should be 
```
**[COLOR="#FF0000"]/[/COLOR]usr/bin/gedit**
```
Works here.

---

### Post by Frogs Hair on 2013-03-13
I can only suggest restarting the browser if you have not. Make sure the setting didn't revert also.

---

### Post by Jameela on 2013-03-18
> **Frogs Hair said:**
> I can only suggest restarting the browser if you have not. Make sure the setting didn't revert also.



Found my mistake!  I inadvertantly put a space before the first slash of:**   /usr/bin/gedit ** 

Works fine now after restarting Firefox

Thanks for the help.

---

