---
title: "Make application start when Ubuntu starts"
date: 2008-06-29
forum: General Help
---

### Post by ka1eui on 2008-06-29
Hello.

I use Gmail and I downloaded "CheckGmail" which is a small application that sits no my task bar and alerts me if I have any mail at Google Mail.

The problem is that I never remember to start it.  How can I make it start when I boot up Ubuntu?

I remember back in the horrible Windoze days that I would just put the application in my Start Folder.  Is there a similar thing I can do with Ubuntu?

thanks!

---

### Post by Canis familiaris on 2008-06-29
Go to System->Preferences->Session
Click Add.

---

### Post by ka1eui on 2008-06-29
OK I see that.....now forgive me please for the dopey question, but how do I find out where my Gmail program is in the files menu?  I hit ADD and now I just need to know where it is residing.

thanks...I'm almost there

---

### Post by dominiquec on 2008-06-29
Usually in the /usr/bin folder.

However, if you want to be really sure, open a terminal and type:

which CheckGmail

That should give you the full path of the program.

---

### Post by Canis familiaris on 2008-06-29
> **ka1eui said:**
> OK I see that.....now forgive me please for the dopey question, but how do I find out where my Gmail program is in the files menu?  I hit ADD and now I just need to know where it is residing.

thanks...I'm almost there

If you have an icon of 'Check Gmail',. Then copy that icon to the desktop, right click it , click on properties and choose the tab launcher.
There you'll find the command required.

EDIT: I think the command should be **checkgmail**

---

### Post by ka1eui on 2008-06-29
Awesome!  Thanks you guys, I learn so much from this forum....

---

