---
title: "home directory with 2 linux?"
date: 2007-06-20
forum: General Help
---

### Post by anarchist_hippy on 2007-06-20
I want to install both Suse and Ubuntu Linux. I know how to install... 

But, I want to know that, can I use the same **/home directory **with both Linux dist. ?

:roll:

Thanks...

---

### Post by llamakc on 2007-06-20
Yes. Make sure to have a separate /home partition.

---

### Post by anarchist_hippy on 2007-06-20
> **llamakc said:**
> Yes. Make sure to have a separate /home partition.

So, after installation, I've one /home directory (partition) and two "/" directory (Suse & ubuntu). And one thing, If I do that, how will be it's performance?

---

### Post by llamakc on 2007-06-20
By "its" precisely what do you mean?

---

### Post by anarchist_hippy on 2007-06-20
I mean that, how will be the performance of the 2 linux with one /home partition ?

---

### Post by llamakc on 2007-06-20
> **anarchist_hippy said:**
> I mean that, how will be the performance of the 2 linux with one /home partition ?

They'll perform as expected? I don't understand what you're inferring. They'll be two separate operating systems that will be dependent on their individual configurations and setup(s), and not on the sharing of the /home/$USER directory. 

Be sure not to reformat the /home partition on the second install of Linux.

The performance will have nothing to do with using one /home. You may have to do some massaging of UID/GUID if the other O/S handles stuff entirely differently.

---

