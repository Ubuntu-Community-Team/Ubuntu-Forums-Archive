---
title: "Multiple log in's"
date: 2007-10-28
forum: General Help
---

### Post by keeler1 on 2007-10-28
After upgrading to 7.10 I am having some very funny issues with logging in.  After getting to the log in and typing the username and password.  The screen starts to go into the desktop but then hangs for a few seconds and throws me back to the login.  I put my info in a second time and then everything works fine.

At first I figured I was just typing it wrong.  So I when I turned my computer on again, I checked to make sure everything was inputted correctly.  However, the problem still exists.

I am at a loss for where to start looking for information on how to fix this.  I searched on the forums and google for a while but found nothing.

Does anyone have any ideas?

---

### Post by Crafty Kisses on 2007-10-28
> **keeler1 said:**
> After upgrading to 7.10 I am having some very funny issues with logging in.  After getting to the log in and typing the username and password.  The screen starts to go into the desktop but then hangs for a few seconds and throws me back to the login.  I put my info in a second time and then everything works fine.

At first I figured I was just typing it wrong.  So I when I turned my computer on again, I checked to make sure everything was inputted correctly.  However, the problem still exists.

I am at a loss for where to start looking for information on how to fix this.  I searched on the forums and google for a while but found nothing.

Does anyone have any ideas?

That's weird try pressing ```
Ctrl+Alt+F2
``` then login from there, and see if it still does it.

---

### Post by keeler1 on 2007-10-29
sorry it took so long to get back with you.  Its been a busy week.

Anyways when I login non-graphically it only takes one try.

---

### Post by keeler1 on 2007-11-01
does anyone have ideas about why it is making me enter the user and pass twice.

---

### Post by keeler1 on 2007-11-03
bump

---

### Post by bingoUV on 2007-11-03
Can you post the contents of ~/.xsession-errors ?

What happens if you log in as another user? To create a user, go to System -> Administration -> Users and Groups

---

### Post by keeler1 on 2007-11-03
I have attached my .xsession-errors file.

---

### Post by keeler1 on 2007-11-05
Within the first couple of lines of my .xsession-errors i noticed something which might be the symptom.  It says a few times that it refused to initialize GTK+ could this be why it wont let me into the desktop without logging in twice.

---

### Post by keeler1 on 2007-11-05
bump

---

### Post by keeler1 on 2007-11-07
Is this happening to anyone else.  I have no clue how to fix it and could use a little help.

---

