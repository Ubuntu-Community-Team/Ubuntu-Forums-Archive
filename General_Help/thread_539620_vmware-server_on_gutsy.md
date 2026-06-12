---
title: "vmware-server on gutsy"
date: 2007-08-31
forum: General Help
---

### Post by ninehrcoma on 2007-08-31
The posts thus far relating to vmware-server on Gutsy have pointed out compiler mis-matches, vmware-any-any versions, and the need for build-essential packages. At least one person in the forums thus far has stated that they are able to run vmware-server when following the steps associated with the previously mentioned requirements.

This is a testing laptop running Gutsy, 2.6.22-10-generic, x86 (Pentium M), and current updates as of 13:22 EST. The vmware-server version being used is 1.0.3-44356, and gcc is symlinked to gcc-4.1. The build-essential package, amongst other various compilers and tools, is installed and the linux-headers are in place.

Upon un-tarring vmware-server and running the installer, I do indeed get the commonly mentioned error of:

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-10-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-10-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.
```


So, I un-tar the vmware-any-any file and run the "runme.pl" script. You can see that it compiles the module and reports that it successfully loads. The process completes and the final message confirms that installation completed successfully.

```
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
The module loads perfectly in the running kernel.

*snip*

The configuration of VMware Server 1.0.3 build-44356 for Linux for this running
kernel completed successfully.

```


However, upon trying to run the vmware program or attempting to restart vmware-server, the following error appears.

```

/etc/init.d/vmware restart
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   Bridged networking on /dev/vmnet2                                   done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done
VMware Server is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

```

One other person mentioned in the forums that they had used 2.6.22-9 with good results, but I get the same problems when booted into the older kernel. Is this a problem that others are having or have solved?

Thanks

---

### Post by Bachstelze on 2007-08-31
[ftp://fkraiem.no-ip.org/pub/vmware](ftp://fkraiem.no-ip.org/pub/vmware)

---

### Post by HermanAB on 2007-08-31
Uhmmm, the answer is right in front of you.  Just read that last line and execute the indicated configuration script and you should be OK.

Cheers,

Herman

---

### Post by ninehrcoma on 2007-08-31
Sorry, maybe I didn't explain that last part well enough. I wish it were that simple. The same error message appears. The runme.pl script merely patches necessary files and runs /usr/bin/vmware-config.pl for you. It doesn't matter how many times you run it, the same problem occurs.

In fact, for clarity:

```

./runme.pl 
Updating /usr/bin/vmware-config.pl ... already patched
Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes]

```

And then it runs..

---

### Post by schmitty2005 on 2007-08-31
I have the EXACT same problem on 7.04 x86 Ubuntu.  It is the same with VMPlayer and VMServer.  Very frustrating.  I would like it to run each time instead of having to reconfigure everything.  If I find a solution, I will post.....been looking for a few hours now.........

---

### Post by dpurple77 on 2007-09-02
This is an old bug and it used to happen with the vmware player installed along with the vmware server. There is a file in /etc/vmware called not_configured. 
If you just delete it by hand everything will be ok. 
so ...
sudo rm /etc/vmware/not_configured

hope that helps.

---

### Post by ninehrcoma on 2007-09-04
Indeed it did work, thanks very much for the help!

---

### Post by cprise on 2007-09-28
I was getting all of the same problems, but upgrading to version 1.0.4 resolved them for me.

---

