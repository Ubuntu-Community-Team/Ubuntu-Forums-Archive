---
title: "cli -list localy installd packages"
date: 2008-01-06
forum: General Help
---

### Post by of_darkness on 2008-01-06
Hi i want to list those packages that are from localy installed .deb:s 
I want 2 do it in terminal so that i can >> into a file.

apt on cd dident list localy installed packages..

---

### Post by p_quarles on 2008-01-06
The following command chain will create such a file:
```
sudo dpkg --get-selections | grep '[[:space:]]install$' | awk '{print $1}' > package_list
```
The first command itself (before the first "|") is the one that lists the installed files.

---

### Post by of_darkness on 2008-01-07
> **p_quarles said:**
> The following command chain will create such a file:
```
sudo dpkg --get-selections | grep '[[:space:]]install$' | awk '{print $1}' > package_list
```The first command itself (before the first "|") is the one that lists the installed files.
Nupp it dosent do the trick.. it lists packages that are in repository..

I want 2 list all installed packages that are NOT in any of my repositorys..

---

### Post by p_quarles on 2008-01-07
I see what you're saying now. I don't believe that's possible, as APT makes no distinction between packages that were installed through the repositories and packages that were installed manually using dpkg.

---

### Post by of_darkness on 2008-01-07
well synaptic list them.. and then the qustion is where the heck dos it find the info.. and howto get it into a list..

---

