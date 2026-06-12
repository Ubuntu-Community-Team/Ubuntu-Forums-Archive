---
title: "Locking down files outside the home directory"
date: 2006-07-10
forum: General Help
---

### Post by huwnet on 2006-07-10
I found a post about locking down Linux systems:

> 
as for locking the users out of the rest of the system, under full linux that is easy you just remove the premisions for the "user" to access anything outside of /home/user_name and you are done.

Is this a good method?

What is the best way of acheiving this?

---

### Post by T700 on 2006-07-10
It's an excellent method.  By default (in all the distros I've seen, anyway), an ordinary user account is created with just such, limited rights.

Paul

---

### Post by taurus on 2006-07-10
Let's say that you have a few users on your system and you don't want them to snoop around your stuff, you change the permission of your $HOME to log them out.  Works like charm...  ;)

---

### Post by huwnet on 2006-07-10
> By default (in all the distros I've seen, anyway), an ordinary user account is created with just such, limited rights. 
Ah, so it is. I should have checked before posting.

> Let's say that you have a few users on your system and you don't want them to snoop around your stuff, you change the permission of your $HOME to log them out. Works like charm... 
Thanks, I'll look into it

---

