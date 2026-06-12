---
title: "Need help with root password"
date: 2007-02-16
forum: General Help
---

### Post by Trey5498 on 2007-02-16
I have installed Ubuntu 6.06 and it never asked me to put in a root pass, just the password for the name I entered.  Now i cant su because I do not know the password to the root.  How do I fix this?

---

### Post by Maestro23 on 2007-02-16
> **Trey5498 said:**
> I have installed Ubuntu 6.06 and it never asked me to put in a root pass, just the password for the name I entered.  Now i cant su because I do not know the password to the root.  How do I fix this?

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by roland_1953 on 2007-02-17
You can perform most administrative functions using the sudo prefix and then entering your admin password.

However, if you absolutely, positively, MUST have access to the root acoount, this is what you do:

 In a console type : [COLOR="Red"]sudo passwd root[/COLOR]

Follow the prompts and enter the new root password.

Viola! You now have a root account.

Be warned, though. You can totally hose your syetem at this level. You should not access the Internet while here.

Regards,
Roger

---

### Post by Trey5498 on 2007-02-17
thank you so much

---

