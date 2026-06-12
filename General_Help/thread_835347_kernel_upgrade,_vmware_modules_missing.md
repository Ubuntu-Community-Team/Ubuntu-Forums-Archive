---
title: "kernel upgrade, vmware modules missing"
date: 2008-06-20
forum: General Help
---

### Post by lamacq on 2008-06-20
Hi All,

Just did an automatic upgrade this morning that included a kernel update and a restart. Am now running  2.6.22-15-generic x86_64. > 

After the restart I went to start up my windows XP VM in VMWare server 1.06, which I installed via synaptic. The VMWare server console starts up just fine, but when I try to resume my VM, I get an error message that says:

> Unable to change virtual machine power state: The process exited with an error: End of error message.

Not very helpful. I took a look and sure enough the vmware server kernel modules are missing for the new kernel:

```
matthew@m-rich:~$ ls -l /lib/modules/2.6.22-14-generic | grep vmware
drwxr-xr-x  2 root root   4096 2008-06-20 09:40 vmware-server
matthew@m-rich:~$ ls -l /lib/modules/2.6.22-15-generic | grep vmware
matthew@m-rich:~$ 
```

I tried reinstalling the vmware server (and vmware kernel modules) packages but I actually got an error during the post install script -- I'm guessing this is because the modules come pre compiled and it errored out trying to load them into a running kernel of a different version.

Help?

---

### Post by f37u5g0d on 2008-06-20
I use virtualbox and right after the kernel upgrade to 2.6.24-18 and 2.6.24-19 I got the same error.  There is a package colled vbox-ose-generic-modules that is updated for each kernel update.  However they for some reason are always slow to update it.  I had to wait about 3 weeks after 2.6.24-18 and I am still waiting for 2.6.24-19 (it's been about a week).  I don't know why they keep doing this.  Kenerel upgrades never effect any other application just this one and it is very annoying as there are about 6 weeks between this level updates.

---

