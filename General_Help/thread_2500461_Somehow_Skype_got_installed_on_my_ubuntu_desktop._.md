---
title: "Somehow Skype got installed on my ubuntu desktop.  I did not install it. Can I delete"
date: 2024-09-02
forum: General Help
---

### Post by Tom_Carr on 2024-09-02
Somehow Skype got installed on my ubuntu desktop.  I did not install it. Can I delete it?

---

### Post by Rubi1200 on 2024-09-02
I've never heard of things just getting installed on Linux. Someone has to install the package for it to be there. And that would require admin access and password.

Skype is not part of any standard Linux install that I am aware of.

So...does someone else have physical access to your computer and also knows the password?

---

### Post by Tom_Carr on 2024-09-02
Then I must have installed it by mistake.  Probably just clicked a button without reading what it did.

---

### Post by Rubi1200 on 2024-09-02
Well, let's figure out where it is and how it was installed so we can uninstall it.

What do these commands show:

```
snap list skype
```

If it is not there, then try this:
```
dpkg -l | grep skype

```

---

### Post by grahammechanical on 2024-09-02
Skype is in Ubuntu Software/App Store and it is a snap packaged app. Find the Skype home page in Ubuntu Software and click the rubbish/dustbin icon to remove it.

Regards

---

