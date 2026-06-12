---
title: "need permenant access to filesystem?"
date: 2008-05-10
forum: General Help
---

### Post by zidane1341 on 2008-05-10
up till recently, i couldn't access my file system folder. i JUST now found out you need to open the terminal, and type in 

gksu nautilus /

now i finally could, but i need to use it a lot, several times a day, and its usually a hassle. is there any way i can get permission to just open up filesystem without the terminal? every time i go in from my computer, and try to add a folder or document, it says its not allowed, something about no permission, which is BS cause i got only one account, and it SHOULD have full permission to do whatever the heck i want. so any help?

---

### Post by Gina on 2008-05-10
That's odd - I can just use nautilus (without gksu) in the GUI.  From Places.  
There must be something wrong in your setup but I can't think what, I'm afraid.

---

### Post by zidane1341 on 2008-05-10
that sucks,when i reinstalled ubuntu,it still wouldnt work

---

### Post by nick_h on 2008-05-11
> i got only one account, and it SHOULD have full permission to do whatever the heck i want.
No. This is a security feature in Ubuntu.  You do have full permissions but only indirectly through gksu, gksudo, sudo.

You could enable the root account but this would be a bad idea.

I suggest that you just create a new nautilus icon for root access, or install the nautilus-gksu package.

---

