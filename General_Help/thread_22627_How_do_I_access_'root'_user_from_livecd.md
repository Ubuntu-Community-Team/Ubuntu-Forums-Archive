---
title: "How do I access 'root' user from livecd?"
date: 2005-03-28
forum: General Help
---

### Post by plonka2000 on 2005-03-28
Hi,

I'm using the Ubuntu LiveCD as a rescue CD and I need to get root user access but I cannot figure out how to: 
1) login as root as I cannot logout of default user.
2) Run Nautilus as root as I cannot find out the root password for the livecd.

Does anyone at least know the root password?

---

### Post by plonka2000 on 2005-03-28
Basically, all I want to do is delete some files from my '/' partition and /boot partition so that I can re-install... I dont want to delete everything.

Can anyone help?

---

### Post by Juanje on 2005-03-29
Well,  Ubuntu use **sudo** for all the administratives task, so basically  you have two ways to do that:
```

# sudo rm /whatever/u/want
Password:
[put your pass here]

```

or

```

# sudo su -
Password:
[put your pass here]
(now you are root)
$ rm /whatever/u/want

```

Bye

Juanje

---

