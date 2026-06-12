---
title: "Apt-get and aptitude"
date: 2007-07-09
forum: General Help
---

### Post by hito1 on 2007-07-09
Is there an equivalent of aptitude's purge, show and search for apt-get?

Can we use aptitude purge (or any other command) with packages installed with apt-get?

Can we configure synaptic to use aptitude? It uses apt-get, right?

Also, does Synaptic shows all packages in the repositories? I searched for lynx in synaptic, but it didn't return any results, I searched with aptitude, and it showed me the packages.

Thanks. :)

---

### Post by mcduck on 2007-07-10
> **hito1 said:**
> Is there an equivalent of aptitude's purge, show and search for apt-get?

"apt-get -purge remove", "apt-get autoremove", "apt-cache search" and "apt-cache show"

> **hito1 said:**
> Can we use aptitude purge (or any other command) with packages installed with apt-get?
You can, but Aptitude only works correctly with packages that were installed with Aptitude in the first place. So you won't get any benefits from doing that.

> **hito1 said:**
> Can we configure synaptic to use aptitude? It uses apt-get, right?
No. Unless you get the source code and modify it yourself. This wouldn't really be useful anyway as they do pretty muchthe same things (only I've found apt-get to be more reliable)

> **hito1 said:**
> Also, does Synaptic shows all packages in the repositories? I searched for lynx in synaptic, but it didn't return any results, I searched with aptitude, and it showed me the packages.
Yes, it does show all packages in all available repositories. Check that you are seaching correctly.

---

### Post by hito1 on 2007-07-10
Thanks for the response. :)

> **mcduck said:**
> 
No. Unless you get the source code and modify it yourself. This wouldn't really be useful anyway as they do pretty muchthe same things (only I've found apt-get to be more reliable)


Indeed, I just wanted to change because I didn't know about apt-get -pruge remove and apt-cache.

---

### Post by dabl on 2007-07-10
> **hito1 said:**
> does Synaptic shows all packages in the repositories?

It shows all packages in the repositories THAT YOU HAVE ENABLED.  But, you might want to check which repositories you have enabled, versus the source for the package that you want.  :)

---

### Post by Rui Pais on 2007-07-10
> **hito1 said:**
> Indeed, I just wanted to change because I didn't know about apt-get -pruge remove and apt-cache.

They are just different frontends for the deeper and harder dpkg. They do more or less the same.

Some people like to install using aptitude and uninstall with apt-get. aptitude has a better dependency manager, it installs recommended packages (contrary to apt-get) and when uninstall removes all related packages installed while apt-get just removes the one(s) you specify. 
A very notorious case being the meta-packages that aptitude can really clean when delete, while apt-get only removes the (empty) meta-package leaving all its packages.

[here]("http://www.psychocats.net/ubuntu/aptitude") some more info.

---

### Post by mcduck on 2007-07-10
> **Rui Pais said:**
> 
A very notorious case being the meta-packages that aptitude can really clean when delete, while apt-get only removes the (empty) meta-package leaving all its packages.

[here]("http://www.psychocats.net/ubuntu/aptitude") some more info.

..and that's why the autoremove option was added to apt-get ;)

'sudo apt-get autoremove packagename' will remove also packages installed as dependencies.

---

### Post by Rui Pais on 2007-07-10
> **mcduck said:**
> ..and that's why the autoremove option was added to apt-get ;)

'sudo apt-get autoremove packagename' will remove also packages installed as dependencies.

yes, i think so. 
I don't know if it deals correctly with big meta-packages like ubuntu-desktop or xubuntu-desktop, never had the opportunity to tried... :)

---

