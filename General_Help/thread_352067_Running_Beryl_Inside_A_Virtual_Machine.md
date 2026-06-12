---
title: "Running Beryl Inside A Virtual Machine"
date: 2007-02-02
forum: General Help
---

### Post by jrickmar on 2007-02-02
I have been seduced by the amazing effects of Beryl, and I would like to run it on my desktop.  The only problem is that I run Kubuntu as a virtual machine with VMWare Workstation on Win XP.

I have gotten the compositing, transparencies, and shadows working with the option in KDE (which I think uses either a plug-in or hack into the X server), so I know that I should be able to do it with Beryl.  I have tried to get it working with the instructions at [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX) but when I try to run beryl-manager, it ends my session and returns to the log in screen with KDM.

Is there some way that I can make Beryl not use AIGLX but instead use the same compositing extension that KDE uses?

---

### Post by Paerez on 2007-02-02
As far as I know, you cannot currently get full graphics card powered 3D rendering within VMWare.

---

### Post by jrickmar on 2007-02-02
Then how did the transparencies/shadows work natively in KDE? :confused:

---

### Post by Paerez on 2007-02-02
I am thinking maybe kde does a software transparency thing rather than hardware.

---

### Post by jrickmar on 2007-02-02
is there any plans for VMWare to add support to graphics card rendering?  If not, I'll just stick with what I have.

---

### Post by Paerez on 2007-02-02
[http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html)

You may need one of the newer CPUs with virtualization technology, but I am not sure.

---

