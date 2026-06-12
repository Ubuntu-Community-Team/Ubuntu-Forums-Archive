---
title: "Root Rights Asks For Pw..But Theres No Pw"
date: 2007-06-19
forum: General Help
---

### Post by Aby on 2007-06-19
Hello Ubu community,

Before all this, i had already tried to login as root, but i couldn't do it, first because it asks for a password, which i have never choosen, so it was impossible for me to login as root. Untill the momment i need, which is now, i didn't bother to figure this out.

Now im trying to make the second monitor to work (both on the same system) but i need to use the cmd "sudo" which is for root privileges as you know, but it asks me that %$&$ password. 

Now, what do you think that happened or is it normal and theres a way to fix this out?

Thanks Ubu's
Hope you can help me
Regards ;)

---

### Post by cogadh on 2007-06-19
It's asking for your password, not root's. That's the way Ubuntu works.

Remember, "There is no Root"... well, sort of.

Let me clarify: Ubuntu does not require you to use a root account. Ubuntu assumes that you, the user, know what you are doing on your own computer and should therefore have the rights to do what you want. However, it won't let you blindly do something you shouldn't, so, certain aspects of the OS are "locked down" in the way that a normal user account is locked down. You get around the lockdown through "sudo" (short for "superuser do") and using your own password.

---

### Post by Aby on 2007-06-19
> **cogadh said:**
> It's asking for your password, not root's. That's the way Ubuntu works.

Remember, "There is no Root"... well, sort of.

Let me clarify: Ubuntu does not require you to use a root account. Ubuntu assumes that you, the user, know what you are doing on your own computer and should therefore have the rights to do what you want. However, it won't let you blindly do something you shouldn't, so, certain aspects of the OS are "locked down" in the way that a normal user account is locked down. You get around the lockdown through "sudo" (short for "superuser do") and using your own password.


Ok, now i get it. My mistake was trying the "su" cmd and even with normal user pw i coulnd't log, but now i understand. Thanks for the help, and it works. :D

Regards,
Aby

---

