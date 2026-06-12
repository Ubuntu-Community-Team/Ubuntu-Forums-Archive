---
title: "kvm will not install, &quot;Dependancy Not Satisfiable&quot;"
date: 2007-01-10
forum: General Help
---

### Post by Belboz99 on 2007-01-10
Hey all,

I'm having a heck of  a time getting Virtualization going at the kernel level.  I've already compiled and booted into the new 2.6.20 kernel.  All I need to do is install kvm and run it...  If only it were that easy. ](*,) 

```
apt-get install kvm
``` responds with: E: Couldn't find package kvm

Downloading the package from [here](http://packages.ubuntu.com/feisty/misc/kvm) results in the Package Installler spitting out:  "Error: Dependency is not satisfiable: libasound2".   However, libasound2 is fully installed, and I have even gone and re-installed it using:

```
sudo apt-get install --reinstall libasound2
```

It still won't install. :(

Anyone have any ideas?

There are no open bugs in kvm, should I report one?

Edit: Here's a screenshot of Package Installer:
[IMG]http://img375.imageshack.us/img375/8495/kvmdg6.png[/IMG]

Thanks,
Dan

---

### Post by Belboz99 on 2007-01-10
Well, it appears that kvm is only available for Feisty Fawn, not Edgy Eft.

Should I upgrade? 

Thanks,
Dan

---

### Post by nhidog on 2007-01-10
I installed it under edgy with the help of this website:

[http://popey.com/Compiling_kvm_Under_Ubuntu_Edgy_i386](http://popey.com/Compiling_kvm_Under_Ubuntu_Edgy_i386)

Seems to be working properly.  I used to use VMWare but for some oddball reason, the application would crash my system after a period of use.  KVM/Qemu has not yet crashed which is a good sign 8) 

Nhi

---

