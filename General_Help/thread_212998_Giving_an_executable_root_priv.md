---
title: "Giving an executable root priv"
date: 2006-07-10
forum: General Help
---

### Post by CujoQuarrel on 2006-07-10
Sorry if this has been covered before but I couldn't find an answer in my search.

How do I go about giving an executable (in this case k3b) root priv for all users? I don't want the user to have to do a *sudo* to run the burner and it doesn't seem to work well on my system unless it has root priv. 

I vaguely rememeber that there is a Unix command for doing something like that.

Thanks in advance
ME

---

### Post by T700 on 2006-07-10
You change the properties of the link to something like:  ```
gksudo k3b
```  That negates the user from having to enter the command to assume root, but they still have to enter a password.

I'd be concerned why someone has to be root to burn a CD.

Paul

---

### Post by RAOF on 2006-07-10
Or, you can find where the binary for k3b is, and add the "sticky" bit to the permissions.  That means that the binary will **always** be run with root privs.  

To do that: **sudo chmod +s */path/to/k3b***

---

### Post by HAARP on 2006-07-11
Wasn't that the user id permission instead of sticky?

---

### Post by digby on 2006-07-11
It is the setuid bit; the sticky bit (as pertains to executable files) is obsolete and (I believe) ignored by the kernel.

---

### Post by RAOF on 2006-07-11
> **digby said:**
> It is the setuid bit; the sticky bit (as pertains to executable files) is obsolete and (I believe) ignored by the kernel.

Quite true.  I always think of "sticky" and "setuid" as the same thing, but they're definitely not.

---

### Post by digby on 2006-07-11
> **RAOF said:**
> Quite true.  I always think of "sticky" and "setuid" as the same thing, but they're definitely not.
Yeah - I just happened to have read about them in a unix administration book a friend loand me the other day, so it was still fresh on my mind...:mrgreen:

---

