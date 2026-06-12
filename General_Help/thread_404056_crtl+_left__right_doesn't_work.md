---
title: "crtl+ left / right doesn't work"
date: 2007-04-07
forum: General Help
---

### Post by Mateo on 2007-04-07
when using the terminal, I can not use crtl+left/right (to move the cursor faster) anymore.  Instead pressing that prints ' ;5D '.

I think it might have something to do with me turning the terminal bell off.  I did this by creating the file ~/.inputrc  with the line "set bell-style none".  I know this seems unrelated, but this started happening right after I did that.

---

### Post by Mateo on 2007-04-11
bump

---

### Post by Mateo on 2007-05-02
bump.

---

### Post by Mateo on 2007-05-02
I think I found a fix for those who are interested.  I think creating a .inputrc file overwrites what is normal.  So I think doing this will fix it:

[http://linuxart.com/log/archives/2005/10/13/super-useful-inputrc/](http://linuxart.com/log/archives/2005/10/13/super-useful-inputrc/)

---

