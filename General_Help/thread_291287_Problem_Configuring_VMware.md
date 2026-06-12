---
title: "Problem Configuring VMware"
date: 2006-11-02
forum: General Help
---

### Post by igb on 2006-11-02
I am having problems setting up VMware workstation 5.5 on Edgy. I have followed the instructions at:

[https://help.ubuntu.com/community/InstallingVMware#head-9973a76766d2a1a45c0da13567ce73c227904cbf]("https://help.ubuntu.com/community/InstallingVMware#head-9973a76766d2a1a45c0da13567ce73c227904cbf")

and it compiles OK. However, when vmware-config.pl runs there are two problems:

If I try to enable NAT it can't find a private subnet, even though one should definitely exist:

```
Probing for an unused private subnet (this can take some time)...

sh: /usr/bin/vmware-ping: not found
sh: /usr/bin/vmware-ping: not found
sh: /usr/bin/vmware-ping: not found
sh: /usr/bin/vmware-ping: not found
sh: /usr/bin/vmware-ping: not found
sh: /usr/bin/vmware-ping: not found
sh: /usr/bin/vmware-ping: not found
sh: /usr/bin/vmware-ping: not found
sh: /usr/bin/vmware-ping: not found
sh: /usr/bin/vmware-ping: not found

```

If I either enter the IP address manually, or even totally disable NAT, as soon as I try to run VMware i get the following error:

```
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
```

I have made sure that I have the latest version of workstation and I have tried uninstalling completely before re-installing. One other factor which may be relevant I am running an AMD64 with 64 bit Edgy.

Ian.

---

### Post by cleentrax on 2006-11-02
I don't get your first problem, but I get your second problem. the configuration script reports a mismatch with the kernel. I am using the latest generic Ubuntu kernel, and the vmware-player from the repos.

---

### Post by chedabob on 2006-11-02
I thought VMware on installed with "vmware-install.pl", and that was it?

---

### Post by oulmanpe on 2006-11-05
I have just encountered this exact same problem installing the latest VMWare server 1.01 on Ubuntu 6.10 (AMD 64). I have even manually copied the vmware-ping executable to the location it appears to be looking for it and set appropriate permissions but I still get the same error. Any help would be greatly appreciated.

Peter

---

### Post by igb on 2006-11-10
I found a solution that works for me on the VMWare forums:

# sudo apt-get install ia32-libs 

I have no idea why it works, but it worked for me:)

Ian.

---

### Post by cephlon on 2006-12-09
I am experiencing the same error. I tried to install ia32-libs, but I get back the message

"E: Couldn't find package ia32-libs"

---

### Post by igb on 2006-12-10
> **cephlon said:**
> I am experiencing the same error. I tried to install ia32-libs, but I get back the message

"E: Couldn't find package ia32-libs"

I suspect that you are missing something in /etc/sources.list. They are definitely there on all my computers.

Ian.

---

### Post by pointym5 on 2007-01-03
> **igb said:**
> I found a solution that works for me on the VMWare forums:

# sudo apt-get install ia32-libs 

I have no idea why it works, but it worked for me:)

Ian.

It works because the "vmware-ping" executable that the VMWare installation kit deploys is a 32-bit executable, not 64-bit.

---

### Post by RemcoBoerma on 2008-06-03
> **igb said:**
> I suspect that you are missing something in /etc/sources.list. They are definitely there on all my computers.

Ian.

Maybe it has to do with what platform exactly you're running. I'm using a 64bit cpu (intel core2 duo) and ```
uname -a
``` reports: ```
Linux remco-desktop 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux
```. 

Could this have to do with a choise in what repositories are available? 

Apt-cache search ia32 doesn't result in any ia32-libs for me as well. (and i do have everything ticked in the software sources.

---

