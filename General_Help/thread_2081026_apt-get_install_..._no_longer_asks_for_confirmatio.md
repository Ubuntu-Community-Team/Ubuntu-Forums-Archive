---
title: "apt-get install ... no longer asks for confirmation"
date: 2012-11-05
forum: General Help
---

### Post by toyfactory on 2012-11-05
I am used to apt-get install ... asking for confirmation [Y/n] before commencing to download new packages.  Recently however it as been assuming Y and automatically starting the download.  The puzzling thing is that it's doing it on two machines, one running Lucid, the other running Precise.  I don't think I've made any changes to the apt config files.  Anyone also have the same problem?  

Similar symptoms to this problem I think:

[http://www.linuxquestions.org/questions/linux-general-1/apt-get-install-does-not-ask-for-confirmation-859586/](http://www.linuxquestions.org/questions/linux-general-1/apt-get-install-does-not-ask-for-confirmation-859586/)

Any ideas?

---

### Post by dannyboy79 on 2012-11-05
i thought it only ever asks you Y/n is when you do sudo aptitude upgrade. When you issue sudo aptitude install foo, it's just gonna do what you asked it to, install the software.

---

### Post by toyfactory on 2012-11-05
I'm pretty sure until a few days ago it would ask for confirmation for install operations as well as upgrade operations.  Can anyone else confirm or is dannyboy79 right and I'm just going crazy?

---

### Post by wheeze on 2012-11-06
> **toyfactory said:**
> I'm pretty sure until a few days ago it would ask for confirmation for install operations as well as upgrade operations.  Can anyone else confirm or is dannyboy79 right and I'm just going crazy?

My experience is with apt-get and not aptitude, but apt-get acts like you were describing. It asks for confirmation for anything, except when you install a single package that doesn't require any dependencies.

---

### Post by Wim Sturkenboom on 2012-11-06
I only occasionally use apt-get to install, but as far as I can remember it has never asked me for confirmation. And for upgrades, it does.

Ubuntu 12.04.

---

### Post by sgage on 2012-11-06
apt-get only asks for confirmation if installing the package(s) you specify requires pulling in dependencies.

---

### Post by SlugSlug on 2012-11-06
> **sgage said:**
> apt-get only asks for confirmation if installing the package(s) you specify requires pulling in dependencies.

+1

---

### Post by wheeze on 2012-11-06
> **sgage said:**
> apt-get only asks for confirmation if installing the package(s) you specify requires pulling in dependencies.

That's what I said.

---

### Post by Wim Sturkenboom on 2012-11-06
> **wheeze said:**
> That's what I said.That's what I thought you said as well :D

---

### Post by toyfactory on 2012-11-07
Thanks everyone.  You learn something new every day!

---

