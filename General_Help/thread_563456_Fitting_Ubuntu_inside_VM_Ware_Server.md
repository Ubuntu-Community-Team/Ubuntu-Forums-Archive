---
title: "Fitting Ubuntu inside VM Ware Server"
date: 2007-09-30
forum: General Help
---

### Post by jfh on 2007-09-30
I have Ubuntu 7.04 installed in a VMWare Server Console, and it seems to be working fine, so far, but I have one small problem.  Although I have both Autofit Host and Autofit Guest checked, the Ubuntu window seems to be a bit too big for the VM Ware window.  I know that I can release the cursor by pressing on Ctrl-Alt, and thus move the Ubuntu Window up and down, but this is minor nuisance which I'd like to avoid.  Is there any way to correct this small problem?

---

### Post by veloce on 2007-10-01
> **jfh said:**
> I have Ubuntu 7.04 installed in a VMWare Server Console, and it seems to be working fine, so far, but I have one small problem.  Although I have both Autofit Host and Autofit Guest checked, the Ubuntu window seems to be a bit too big for the VM Ware window.  I know that I can release the cursor by pressing on Ctrl-Alt, and thus move the Ubuntu Window up and down, but this is minor nuisance which I'd like to avoid.  Is there any way to correct this small problem?

The "solution" is to install vmware-tools. 

However, if you manage this you're doing better than me!

I've tried several different ways and sometimes have managed to get parts of it working by accident - including the autofit guest feature.

---

### Post by bodhi.zazen on 2007-10-02
LOL

vmware-tools is installed on the guest and it is err ... a pain 

I personally used alien, although you do not need to do this.

Follow these directions :

[https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)

OK, now that they are installed, you need them running all the time.

```
vmware-toolbox
``` in a terminal. You can minimize, but not close that dialog box :twisted:

---

