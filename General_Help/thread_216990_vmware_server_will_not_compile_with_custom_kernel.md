---
title: "vmware server will not compile with custom kernel"
date: 2006-07-16
forum: General Help
---

### Post by reacocard on 2006-07-16
I am using a custom kernel compiled with suspend2 support (got it from [here]("http://dagobah.ucc.asn.au/dapper-kernels/")), and the vmware server kernel modules will not compile. i have the kernel headers installed, but all i get are compiler errors. i've searched these forums but haven't found anything that works. any ideas? thanks in advance.

kernel: 2.6.15-26-686-nosmp
vmware server: v1.0

---

### Post by [S|G] on 2006-07-16
I'm also using a custom kernel (2.6.17-ck1) and vmware told me it couldn't find the headers. After googling a bit, I found that I had to modify some of its scripts in order to get it working.

Can you paste the error messages? I can't recall exactly what I did now, but I donwloaded a package that contained the corrected scripts. While I don't have them on my computer anymore, if I take a look at the error I'm sure I can find it again.

---

### Post by reacocard on 2006-07-16
there are more eroors than fit in the terminal. last bit:

```
/tmp/vmware-config7/vmmon-only/linux/driver_compat2.h: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config7/vmmon-only/linux/driver_compat2.h:1619: error: dereferencing pointer to incomplete type
/tmp/vmware-config7/vmmon-only/linux/driver_compat2.h:1702: error: ‘EINVAL’ undeclared (first use in this function)
/tmp/vmware-config7/vmmon-only/linux/driver.c: In function ‘LinuxDriverError’:
/tmp/vmware-config7/vmmon-only/linux/driver.c:2274: error: ‘current’ undeclared (first use in this function)
make[2]: *** [/tmp/vmware-config7/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config7/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-686-nosmp'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config7/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


```

---

### Post by [S|G] on 2006-07-16
[http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update101.tar.gz](http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update101.tar.gz)
There you go. Updating the files "vmmon.tar" and "vmnet.tar" solved the problem here. You can take a look at these threads to understand what is happening:

[http://www.vmware.com/community/thread.jspa?threadID=36156&start=30&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=36156&start=30&tstart=0)
[http://www.vmware.com/community/thread.jspa?threadID=36580&tstart=325](http://www.vmware.com/community/thread.jspa?threadID=36580&tstart=325)
[http://www.vmware.com/community/thread.jspa?threadID=36866&tstart=100](http://www.vmware.com/community/thread.jspa?threadID=36866&tstart=100)

---

### Post by reacocard on 2006-07-16
you use it by running runme.pl correct? it doesn't work. same error.

---

### Post by [S|G] on 2006-07-16
runme.pl didn't work for me. I manually substituted the vmmon.tar and vmnet.tar in vmware directory (I can't recall exactly where they are, but you can find them doing a search) then running vmware-config.pl again.

---

### Post by reacocard on 2006-07-17
i replaced the files in the installer before i installed, but it's still not working. any more ideas?

---

### Post by [S|G] on 2006-07-17
> **reacocard said:**
> i replaced the files in the installer before i installed, but it's still not working. any more ideas?

I'm attaching my vmware-config.pl. Try to backup your old one and use this one instead. I've made some changes so it wouldn't check for a parameter on the kernel source that has changed on the latest kernels (I believe that it was mentioned in one of those links I posted earlier).

---

### Post by reacocard on 2006-07-17
still nothing

---

### Post by [S|G] on 2006-07-17
Can you paste the whole output of your vmware-config.pl command? Try this:
```
sudo /PathToVmware/vmware-config.pl > /home/YourUser/output.txt
```
That will redirect the output to a file called "output.txt" in your home folder, and then you can copy and paste easily here.

---

### Post by reacocard on 2006-07-17
k, didn't know that trick. any way to make it display the text output in the terminal too? the file is attached. apparently the make errors didn't go to the file, they went to the terminal instead.

---

