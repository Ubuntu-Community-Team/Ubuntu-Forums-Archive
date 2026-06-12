---
title: "VMWare Workstation problem"
date: 2007-08-22
forum: General Help
---

### Post by ashughes on 2007-08-22
I have a strange problem with VMWare Workstation 6.  I can get it installed ok, but the problem is, it appears to be installing VMWare Player as well.  This poses a problem because every time I reboot, the two are conflicting and causing me to rerun the configuration script just so I can launch Workstation.

Any ideas.

---

### Post by fppl on 2007-08-22
Keep your vmware workstation installation.

uninstall ur current one + all your vmware player installations.

install vmware workstation only

---

### Post by ashughes on 2007-08-23
I have no vmware player installations.  here is what I did.

1. Install Ubuntu
2. Download VMWare Workstation from vmware.com
3. Extract VMWare Workstation zip
4. Run vmware-install.pl

This installs both player and workstation even though I have only downloaded workstation.  Is it possible that VMWare is bundling the two together for some reason?

---

### Post by cambie on 2007-08-23
They come bundled together, and this is not an issue. I have both vmware workstation and player installed on every linux box I use Vmware on. None exhibit this problem.

I just set up workstation 6 64bit on a new AMD box I built the other day, Ubuntu 7.04. I assume you ran the ./vmware-install.pl script as root, right? And when it asked you if you wanted to configure, did you say yes? if not, you need to run vmware-configure.pl as root.

After this, you should only have to rerun the configure script when your kernel gets updated again. Everytime the kernel is updated, you have to reconfigure. Other than that, you shouldn't have a problem. Post back if none of this helps.

---

### Post by ashughes on 2007-08-23
yes, when I installed it I ran as root.  I just run everything as root by default now.  It is just easier that way.  It appears they are behaving with eachother now.  I am not sure what I did.  I better shut up before I jynx it.

---

### Post by gairy_s on 2008-02-16
> **cambie said:**
> 
After this, you should only have to rerun the configure script when your kernel gets updated again. Everytime the kernel is updated, you have to reconfigure. Other than that, you shouldn't have a problem. Post back if none of this helps.

I am guessing this is where my problem is. I did the install and began the config and I got this:

Do you wish to configure another host-only network? (yes/no) [no] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
/tmp/vmware-config0/vmnet-only/userif.c: In function ‘VNetCopyDatagramToUser’:
/tmp/vmware-config0/vmnet-only/userif.c:630: error: ‘const struct sk_buff’ has no member named ‘h’
/tmp/vmware-config0/vmnet-only/userif.c:630: error: ‘const struct sk_buff’ has no member named ‘nh’
/tmp/vmware-config0/vmnet-only/userif.c:636: error: ‘const struct sk_buff’ has no member named ‘h’
make[2]: *** [/tmp/vmware-config0/vmnet-only/userif.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


I will restart then try to config again.

---

### Post by gairy_s on 2008-02-16
I am not sure if this will help, but I found a solution that let me finish the config, although I haven't tried to run it yet. I am posting this so hopefully it may help someone else.

[http://communities.vmware.com/message/627805#627805](http://communities.vmware.com/message/627805#627805)

I am unaware of any problems this installer may cause, but it worked for me.

---

