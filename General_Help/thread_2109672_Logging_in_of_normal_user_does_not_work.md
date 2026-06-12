---
title: "Logging in of normal user does not work"
date: 2013-01-28
forum: General Help
---

### Post by kevincmaker on 2013-01-28
Hello,
I'm using Ubuntu 12.10 and recently I changed my password via the ubuntu shell (by editing the GRUB). Now, when I try to login, the screen blinks for a second (like it's working normal) but still remains in the same page.

But, when I try to login via the guest account, it works. I saw many people having the same problem but they don't work. Even if I can't correct it, I want to know why this occurs (as I'm a rookie in using Ubuntu ):P ). Any help would be appreciated!

Edit : I deleted the .Xauthority file as one suggested and so now another file with the same name exists but nothing is inside it.

---

### Post by dino99 on 2013-01-28
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by kevincmaker on 2013-01-28
> **dino99 said:**
> [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

@dino99,

Tried remounting as in the given link but still have the  same problem. My friend also tried the same thing (changed the password  from the root shell via GRUB) and now, he too faces the same problem.

Surely,  changing the password from the root shell has something to do with  this. May be this is a bug in Ubuntu 12.10. Any other suggestions?

---

### Post by steeldriver on 2013-01-28
I'm confused what you did exactly - changing your user's login password should not involve "editing the GRUB" - if you set a grub (boot) password that is something completely different

---

