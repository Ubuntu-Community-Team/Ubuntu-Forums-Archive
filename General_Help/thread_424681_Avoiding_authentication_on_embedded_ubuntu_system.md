---
title: "Avoiding authentication on embedded ubuntu system"
date: 2007-04-26
forum: General Help
---

### Post by peterg on 2007-04-26
I'm looking for a way to start Xubuntu feisty without authentication. Security is not a concern. I'm aware of this tutorial: [http://doc.gwos.org/index.php/Automatic_Login_No_Authentication](http://doc.gwos.org/index.php/Automatic_Login_No_Authentication) 

I followed the instructions to the letter, but gcc returned the following cryptic error message:

autologin.c: In function ‘main’:
autologin.c:4: warning: incompatible implicit declaration of built-in function ‘execlp’

Can anyone tell me what I might be doing wrong, or perhaps even come up with a better way of doing this?

Regards,

Peter G

---

### Post by Jarn on 2007-04-26
Couldn't you just set your login manger to auto-login? I know you can with KDM and I would assume most have that feature.

---

### Post by peterg on 2007-04-27
There doesn't appear to be any such feature...

---

