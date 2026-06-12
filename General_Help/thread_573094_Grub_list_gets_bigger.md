---
title: "Grub list gets bigger"
date: 2007-10-11
forum: General Help
---

### Post by jjb123 on 2007-10-11
I everyone, 
I installed Kubuntu about a month ago and so far everything is going great, but I have one small question. Every time there is a kernel update my grub list keeps getting bigger. Is there a way I can have it so that the new kernel option is added and the old one is removed or something like that?

Thank you.

---

### Post by Forlong on 2007-10-11
If you have tested thoroughly that the latest kernel works for you, it's safe to remove the old one(s) (e.g. via Adept)

The menu.lst (for GRUB) will get updated automatically.

---

### Post by RyanthePenguin on 2008-04-15
Please forgive the stupid question.  I am guessing that I just write down the old kernel name and search for it in Adept or Synaptic?  Again, it may sound stupid, but I'd rather not thrash the current install.  I just had to dump Hardy and start fresh with Gutsy again.

---

### Post by roachk71 on 2008-04-16
It's generally a very good (and safe) idea to keep at least one older kernel installed, in case the new one develops issues.

The very old kernels are simply wasting space, and should be safe to remove.

---

### Post by Forlong on 2008-04-16
> **RyanthePenguin said:**
> Please forgive the stupid question.  I am guessing that I just write down the old kernel name and search for it in Adept or Synaptic?
Go to Synaptic or Adept and search for **linux-image**
This will list all kernels available.

---

### Post by Oldsoldier2003 on 2008-04-16
> **Forlong said:**
> Go to Synaptic or Adept and search for **linux-image**
This will list all kernels available.

In Synaptic you have to make sure you mark it for complete removal in order for all the extra kernel dependencies plus the grub menu listing to be cleared. I'm not sure about in adept, but take an extra second to be sure.

---

