---
title: "Help compiling VPN software"
date: 2006-08-22
forum: General Help
---

### Post by scratched on 2006-08-22
I am trying to install Cisco VPN software on my laptop for school and I'm having trouble getting the software to make/compile.

Part of the installation setup requires the directory containing the linux kernel. I tried giving entering in the directory:
```
/usr/src/linux-source-2.6.15
```
but when it began compiling the software came up with a plethora of errors and warnings and it couldn't finish.

The software is designed for RedHat and Solaris but it (supposedly) can work on other Linux distros (I have no proof of that so far other than a sentence in Cisco's documentation) The documentation states:
> The VPN client for Linux supports Red Hat Version 6.2 Linux (Intel), or compatible libraries with glibc Version 2.1.1-6 or later, using kernel Versions 2.2.12 or later.
I'm not sure if I have the glibc since I couldn't find anything by that name in synaptic and I don't know exactly what else it could be called (I do have the gcc however and I've compiled a few things before on this laptop)

The installation says this when it asks for the kernel directory:
> In order to build the VPN kernel module, you must have the kernel headers for the version of the kernel you are running.

For RedHat 6.x users these files are installed in /usr/src/linux by default
For RedHat 7.x users these files are installed in /usr/src/linux-2.4 by default
For Suse 7.3 users these files are installed in /usr/src/linux-2.4.10.SuSE by default

Directory containing linux kernel source code []

I'm not sure if I'm giving the wrong directory for the kernel source or if the software just can't be installed on ubuntu but I was hoping someone on these forums might know what I could have done wrong.

---

### Post by yoder on 2006-08-23
I'm having the same problems.  I seem to remember that what the Cisco client is looking for is in the lib directory, but not positive.  I'm Googling because I know I've seen the fix before.

---

### Post by kernelpanicked on 2006-08-23
The cisco client has some serious issues. I would suggest simplifying your life and installing vpnc.

---

### Post by scratched on 2006-08-23
> **kernelpanicked said:**
> I would suggest simplifying your life and installing vpnc.
I'm not sure if I can. The Cisco client is provided by my school and I don't know if another client will work on their network (I need it to use their wifi)

I'll give vpnc a try but I can't really test it out until school starts 2 weeks from now. Anyone have any solutions to the Cisco client until then?

---

