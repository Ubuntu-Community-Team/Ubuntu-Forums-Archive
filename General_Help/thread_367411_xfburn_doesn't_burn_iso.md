---
title: "xfburn doesn't burn iso"
date: 2007-02-22
forum: General Help
---

### Post by jmvidalvia on 2007-02-22
When I try to burn an iso, just doesn't do anything.
In ouitput, I can read:
Use	cdrecord dev=help
to get a list of possible SCSI transport specifiers.

Any idea about how to make it run?
Thanks!

---

### Post by kerry_s on 2007-02-22
The one in edgy is broken. You can use the one from dapper-> [http://mirrors.kernel.org/ubuntu/pool/main/x/xfburn/xfburn_0.0.3svn+r21611-0ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/x/xfburn/xfburn_0.0.3svn+r21611-0ubuntu2_i386.deb)
Make sure you uninstall the old edgy xfburn first.

---

### Post by jmvidalvia on 2007-02-22
Thank you very much!
How don't they replace in the repositories the wrong program to right one, althought it's the old version, while it is being fixed?

---

### Post by jmvidalvia on 2007-02-22
When I try to remove xfburn (via synaptic or apt-get), system says it will also remove xubuntu-desktop!
Isn't xubuntu-desktop my desktop application?
Should I remove it? It sounds dangerous!
Thanks!

---

### Post by kerry_s on 2007-02-22
xubuntu-desktop is just a meta package, it's safe to remove. It's just of list of application that make up xubuntu-desktop, it's for during the install of xubuntu.

---

### Post by sardion on 2007-02-22
I disagree.  Uninstalling xubuntu-desktop will cause problems if you try to upgrade when feisty comes out.

If you really want to use xfburn, do as said before, remove the old one (and xubuntu-desktop) and install from dapper.  Just be sure to aptitude install xubuntu-desktop before you try to upgrade to feisty.

That said, xfburn may or may not be included in xubuntu in the future so you may want to consider using gnomebaker or something else instead.

---

### Post by kerry_s on 2007-02-22
I disagree. The best way to update to feisty is a clean install. There have been so many changes, that if you want to have a trouble free system, it's best to start clean. And gnomebaker, why would someone want all those dependencys, more gnome parts to slow everything down. :confused:

---

### Post by jmvidalvia on 2007-02-23
Thanks for the discussion, guys!
Now everything is clear.
I will use xfburn from dapper (I prefer light applications, althoug I have a powerfull machine) , remove xubuntu-desktop, and won't update from edgy to dapper.
Good thing of Linux: you can choose!
Many thanks!

---

