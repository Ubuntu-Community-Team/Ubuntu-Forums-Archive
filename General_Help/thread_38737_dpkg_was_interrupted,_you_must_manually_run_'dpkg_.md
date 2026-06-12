---
title: "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the prob"
date: 2005-06-01
forum: General Help
---

### Post by mila80 on 2005-06-01
Hi all,
  I was install some application as xmms and k3b and more with apt, but I can't do it because the system return me this error:

[FONT=Impact][COLOR=Red]dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
[/COLOR][/FONT]

How can I solve this problem?

Thanks, Ma :roll: rco

---

### Post by bored2k on 2005-06-01
[QUOTE=mila80]Hi all,
  I was install some application as xmms and k3b and more with apt, but I can't do it because the system return me this error:

[FONT=Impact][COLOR=Red]dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
[/COLOR][/FONT]

How can I solve this problem?

Thanks, Ma :roll: rco[/QUOTE]
 > run 'dpkg --configure -a' to correct the problem.
```
sudo dpkg --configure -a
```

---

### Post by mila80 on 2005-06-02
[QUOTE=bored2k]```
sudo dpkg --configure -a
```[/QUOTE]
 ok, very well, but now I'm going to try...
thanks

---

### Post by Monk22 on 2006-10-21
i had the same problem i ran "dpkg --configure -a" but the problem is i tried to install setiathome but the link is broken so it keeps trying to connect over and over. so how do i make it stop trying to install setiathome

---

