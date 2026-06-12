---
title: "VMware stuck?"
date: 2007-02-05
forum: General Help
---

### Post by Norfolk 'n' Good on 2007-02-05
Hi,

I had VMware working fine the other day; such a dream to have Ubuntu with XP running flawlessly inside it. However, I recently reinstalled Ubuntu onto a new hard drive and tried to reinstall VMware, but I keep getting the following message when I try to launch it. It's the same copy of Ubuntu (Edgy 6.10 AMDX64). The only thing that's changed,apart from the hard drive, is a new monito

```

root@ubuntu64:/usr/bin# ./vmware /usr/bin/ldd: line 171: /lib/ld-linux.so.2: No such file or directory ldd: /lib/ld-linux.so.2 exited with unknown exit code (127) /usr/lib/vmware/lib/wrapper-gtk24.sh: line 142: /usr/lib/vmware/bin/vmware: No such file or directory /usr/bin/ldd: line 171: /lib/ld-linux.so.2: No such file or directory ldd: /lib/ld-linux.so.2 exited with unknown exit code (127) /usr/lib/vmware/lib/wrapper-gtk24.sh: line 142: /usr/lib/vmware/bin/vmware: No such file or directory root@ubuntu64:/usr/bin#

``` 

Any help would be much appreciated.

Thank you

---

### Post by MoLE on 2007-02-11
Which version of vmware are you using? Player or server or workstation?  Did you install using the repositories?
Your error message seems to indicate it didn't install completely, as there are multiple missing files.

---

### Post by veloce on 2007-02-11
Yeah, need to know if it's player or server.

If its player and you are installing from the repositories then I think the latest kernel upgrade has killed it.  

Server requires you to re-run vmware-config which, among other things, recompiles some stuff for the current kernel version.

I suspect that the vmware player in the repositories is not compatible with the latest kernel. So if your latest Ubuntu install has been updated to the new kernel, then this could be your problem.

Does this help?  If not, more info please! :)

---

