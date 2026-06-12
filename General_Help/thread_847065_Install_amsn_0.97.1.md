---
title: "Install amsn 0.97.1"
date: 2008-07-02
forum: General Help
---

### Post by Sportingfan on 2008-07-02
Hi all,

i just tried installing the new amsn 0.97.1 but i received an error while installing the auto-package.
```

Checking for required C library versions ... OK
Error: Unable to prepare package AMSN MSN client.
```

I also tried installing threw the terminal.
```
package install amsn-0.97.1-1.tcl84.x86.package
```
and this was returned:
```
/tmp/autopackage.284839130/meta/@amsn-project.net/amsn:0.97.1/apkg-prep-install-script: line 127: _checkEULA: command not found
```

Any idea what to do?

I checked my system for tcl/tk and 8.4 is installed.

---

### Post by jolx on 2008-07-02
i believe u need tlc/tk 8.5 installed

and [this]("http://www.amsn-project.net/wiki/FAQ#TLS_does_not_seem_to_work_and_I_have_tcl.2Ftk_8.5._How_can_I_fix_it_.3F") may help

---

### Post by Claus7 on 2008-07-02
Hello,

why not try and have an eye candy amsn?
[http://ubuntuforums.org/showthread.php?t=712425](http://ubuntuforums.org/showthread.php?t=712425)
and it is pretty easy!

Regards!

---

### Post by Sportingfan on 2008-07-02
> **jolx said:**
> i believe u need tlc/tk 8.5 installed

and [this]("http://www.amsn-project.net/wiki/FAQ#TLS_does_not_seem_to_work_and_I_have_tcl.2Ftk_8.5._How_can_I_fix_it_.3F") may help

The line they suggest to replace is already how it should be.

---

### Post by Claus7 on 2008-07-03
Hello,

I think that you should install the latest tcl and tk libraries... You can do that either from synaptic or yourself.See in synaptic if you have the latest versions checked and if not upgrade accordingly.

Searching a little, what I can make out is that this happens due to a library incompatibility. Either the version you have is very old, or even though it might be the right version, your ubuntu version is old and it causes some problems. 

Judging from these links I guess that you should compile yourself at least the tcl library and then try to install the source package unless synaptic solves your problems.
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=652935](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=652935)
[http://forum.eeeuser.com/viewtopic.php?id=1225](http://forum.eeeuser.com/viewtopic.php?id=1225)
[http://ubuntuforums.org/showthread.php?t=625821](http://ubuntuforums.org/showthread.php?t=625821)

Regards!

---

