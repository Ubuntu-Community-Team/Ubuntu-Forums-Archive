---
title: "Add/Remove applications."
date: 2007-03-09
forum: General Help
---

### Post by millerdc on 2007-03-09
I would like to remove things like Gimp but it tells me I need to use synaptic. Synaptic wants to also remove ubuntu-desktop along with Gimp. This is obviously bad. Why would they even have Gimp in Add/remove applications if you can't remove it? Is there another way to remove things like Gimp and OOffice without removing anything else?

Thanks.

---

### Post by llamakc on 2007-03-09
Because it is not obviously bad. The package ubuntu-desktop is a meta-package that REFERS to many, many other packages. 

You can safely remove it. However, if new packages are added to the meta-packages list, you will not have them installed. Removing ubuntu-desktop won't break anything.

---

### Post by moore.bryan on 2007-03-09
*and if you're planning to update the system from edgy to feisty, you'll need it.  why would you want to get rid of gimp?*

---

### Post by millerdc on 2007-03-09
> **moore.bryan said:**
> *and if you're planning to update the system from edgy to feisty, you'll need it.  why would you want to get rid of gimp?*

Because I never use Gimp or Ooffice. I could use the free space for other data. Doesn't anyone else find it pointless to have things like OOffice, Evolution, Gimp, etc, in Add/remove applications if it can't remove them?

---

### Post by moore.bryan on 2007-03-09
*do you abiword instead?  i agree with you on evolution, but i like gimp around just in-case.  none of them take huge amounts of space; is space that much of an issue?*

---

### Post by llamakc on 2007-03-09
If I were to find it pointless I would probably do a server install and then build my packages up from there, installing only what I wanted at that time.

So no, I don't find it pointless that Ubuntu packages a desktop alternative that is pregnant with choice and available software.

Also, it CAN remove them. It tells you precisely how to also. When you went to do so, you were told "ubuntu-desktop" would need to be removed, which as I mentioned is not obviously bad. It is the way Ubuntu manages the wealth of packages which are provided by ubuntu-desktop, kubuntu-desktop, xubuntu-desktop.

Why not just remove the metapackage and then whatever else you want?

---

