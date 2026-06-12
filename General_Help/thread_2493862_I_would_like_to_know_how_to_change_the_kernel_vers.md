---
title: "I would like to know how to change the kernel version of Ubuntu."
date: 2023-12-27
forum: General Help
---

### Post by rnakama on 2023-12-27
Currently, the kernel version of Ubuntu 22.04 used in the Azure virtual machine is "6.2.0-1016-azure", but the kernel version can be changed from "6.2.0-1016-azure" to "6.2.0-azure". I would like to know the command to change to "1018-azure". Thank you. Also, if I change the kernel version, do I need to restart the OS?

$uname -r
6.2.0-1016-azure

$sudo apt-cache search linux-image-6.
linux-image-6.2.0-1018-azure - Signed kernel image azure

---

### Post by TheFu on 2023-12-27
a) if you change the kernel, yes, you need to restart the system.
b) You can't just change the name of the kernel. You have to change the actual kernel used.  I've never used Azure, but seems you need to use an Azure specific kernel there. I suspect they either manage it for you or have repository where you can get a list of available packages.

```
$ apt search  'linux-image' |grep '\-6.'
```
shows a list for me, signed and unsigned.

*linux-image-unsigned-6.2.0-1018-azure* is the package name I think you want. You'll need the matching headers, modules  and DKMS stuff too, almost certainly.

---

### Post by MAFoElffen on 2023-12-27
You can use wildcards to get that closer:
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt list linux-image-6*-azure
Listing... Done
linux-image-6.2.0-1005-azure/jammy-updates,jammy-security 6.2.0-1005.5~22.04.1+1 amd64
linux-image-6.2.0-1006-azure/jammy-updates,jammy-security 6.2.0-1006.6~22.04.1 amd64
linux-image-6.2.0-1007-azure/jammy-updates,jammy-security 6.2.0-1007.7~22.04.1 amd64
linux-image-6.2.0-1008-azure/jammy-updates,jammy-security 6.2.0-1008.8~22.04.1 amd64
linux-image-6.2.0-1011-azure/jammy-updates,jammy-security 6.2.0-1011.11~22.04.1 amd64
linux-image-6.2.0-1012-azure/jammy-updates,jammy-security 6.2.0-1012.12~22.04.1 amd64
linux-image-6.2.0-1014-azure/jammy-updates,jammy-security 6.2.0-1014.14~22.04.1 amd64
linux-image-6.2.0-1015-azure/jammy-updates,jammy-security 6.2.0-1015.15~22.04.1 amd64
linux-image-6.2.0-1016-azure/jammy-updates,jammy-security 6.2.0-1016.16~22.04.1 amd64
linux-image-6.2.0-1017-azure/jammy-updates,jammy-security 6.2.0-1017.17~22.04.1 amd64
linux-image-6.2.0-1018-azure/jammy-updates,jammy-security 6.2.0-1018.18~22.04.1 amd64
linux-image-6.5.0-1007-azure/jammy-updates,jammy-security 6.5.0-1007.7~22.04.1 amd64
linux-image-6.5.0-1009-azure/jammy-updates,jammy-security 6.5.0-1009.9~22.04.1 amd64
linux-image-6.5.0-1010-azure/jammy-updates 6.5.0-1010.10~22.04.1 amd64

```
You have only those choices... Unless the machine on your Azure machine is a different arch or release. You could run that same command, as posted, to show what is available for your's.

Then once you get the version of what you want to install, use that version to search again. Why? Because to install a kernel, you need the 4 packages of that kernel is made from: linux-image-<version>, linux-headers-<version>, linux-modules-<version>, and linux-modules-extra-<version>... Like this:
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt list linux*-6.2.0-1018-azure* | grep -v 'nvidia\|tools'

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

Listing...
linux-buildinfo-6.2.0-1018-azure/jammy-updates,jammy-security 6.2.0-1018.18~22.04.1 amd64
linux-headers-6.2.0-1018-azure/jammy-updates,jammy-security 6.2.0-1018.18~22.04.1 amd64
linux-image-6.2.0-1018-azure-fde/jammy-updates,jammy-security 6.2.0-1018.18~22.04.1.1 amd64
linux-image-6.2.0-1018-azure/jammy-updates,jammy-security 6.2.0-1018.18~22.04.1 amd64
linux-image-unsigned-6.2.0-1018-azure-fde/jammy-updates,jammy-security 6.2.0-1018.18~22.04.1.1 amd64
linux-image-unsigned-6.2.0-1018-azure/jammy-updates,jammy-security 6.2.0-1018.18~22.04.1 amd64
linux-modules-6.2.0-1018-azure/jammy-updates,jammy-security 6.2.0-1018.18~22.04.1 amd64
linux-modules-extra-6.2.0-1018-azure/jammy-updates,jammy-security 6.2.0-1018.18~22.04.1 amd64

```
So an example command from that output might be like:
```

sudo apt install -y linux-headers-6.2.0-1018-azure linux-image-6.2.0-1018-azure linux-modules-6.2.0-1018-azure linux-modules-extra-6.2.0-1018-azure

```

---

### Post by TheFu on 2023-12-27
The list I saw has some other things between the kernel version and "linux-image" ... so I forced grep to output all of the answers that started with 'linux-image' and filtered using egrep.

---

### Post by MAFoElffen on 2023-12-27
Yes, true... (but are not used much, by many)
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt list linux-image*-6*-azure*
Listing... Done
linux-image-6.2.0-1005-azure/jammy-updates,jammy-security 6.2.0-1005.5~22.04.1+1 amd64
linux-image-6.2.0-1006-azure/jammy-updates,jammy-security 6.2.0-1006.6~22.04.1 amd64
linux-image-6.2.0-1007-azure/jammy-updates,jammy-security 6.2.0-1007.7~22.04.1 amd64
linux-image-6.2.0-1008-azure-fde/jammy-updates,jammy-security 6.2.0-1008.8~22.04.1.1 amd64
linux-image-6.2.0-1008-azure/jammy-updates,jammy-security 6.2.0-1008.8~22.04.1 amd64
linux-image-6.2.0-1009-azure-fde/jammy-updates,jammy-security 6.2.0-1009.9~22.04.3.1 amd64
linux-image-6.2.0-1011-azure-fde/jammy-updates,jammy-security 6.2.0-1011.11~22.04.1.1 amd64
linux-image-6.2.0-1011-azure/jammy-updates,jammy-security 6.2.0-1011.11~22.04.1 amd64
linux-image-6.2.0-1012-azure-fde/jammy-updates,jammy-security 6.2.0-1012.12~22.04.1.1 amd64
linux-image-6.2.0-1012-azure/jammy-updates,jammy-security 6.2.0-1012.12~22.04.1 amd64
linux-image-6.2.0-1014-azure-fde/jammy-updates,jammy-security 6.2.0-1014.14~22.04.1.1 amd64
linux-image-6.2.0-1014-azure/jammy-updates,jammy-security 6.2.0-1014.14~22.04.1 amd64
linux-image-6.2.0-1015-azure-fde/jammy-updates,jammy-security 6.2.0-1015.15~22.04.1.1 amd64
linux-image-6.2.0-1015-azure/jammy-updates,jammy-security 6.2.0-1015.15~22.04.1 amd64
linux-image-6.2.0-1016-azure-fde/jammy-updates,jammy-security 6.2.0-1016.16~22.04.1.1 amd64
linux-image-6.2.0-1016-azure/jammy-updates,jammy-security 6.2.0-1016.16~22.04.1 amd64
linux-image-6.2.0-1017-azure-fde/jammy-updates,jammy-security 6.2.0-1017.17~22.04.1.1 amd64
linux-image-6.2.0-1017-azure/jammy-updates,jammy-security 6.2.0-1017.17~22.04.1 amd64
linux-image-6.2.0-1018-azure-fde/jammy-updates,jammy-security 6.2.0-1018.18~22.04.1.1 amd64
linux-image-6.2.0-1018-azure/jammy-updates,jammy-security 6.2.0-1018.18~22.04.1 amd64
linux-image-6.5.0-1007-azure/jammy-updates,jammy-security 6.5.0-1007.7~22.04.1 amd64
linux-image-6.5.0-1009-azure-fde/jammy-updates,jammy-security 6.5.0-1009.9~22.04.1 amd64
linux-image-6.5.0-1009-azure/jammy-updates,jammy-security 6.5.0-1009.9~22.04.1 amd64
linux-image-6.5.0-1010-azure-fde/jammy-updates 6.5.0-1010.10~22.04.1 amd64
linux-image-6.5.0-1010-azure/jammy-updates 6.5.0-1010.10~22.04.1 amd64
linux-image-unsigned-6.2.0-1005-azure/jammy-updates,jammy-security 6.2.0-1005.5~22.04.1 amd64
linux-image-unsigned-6.2.0-1006-azure/jammy-updates,jammy-security 6.2.0-1006.6~22.04.1 amd64
linux-image-unsigned-6.2.0-1007-azure/jammy-updates,jammy-security 6.2.0-1007.7~22.04.1 amd64
linux-image-unsigned-6.2.0-1008-azure-fde/jammy-updates,jammy-security 6.2.0-1008.8~22.04.1.1 amd64
linux-image-unsigned-6.2.0-1008-azure/jammy-updates,jammy-security 6.2.0-1008.8~22.04.1 amd64
linux-image-unsigned-6.2.0-1009-azure-fde/jammy-updates,jammy-security 6.2.0-1009.9~22.04.3.1 amd64
linux-image-unsigned-6.2.0-1011-azure-fde/jammy-updates,jammy-security 6.2.0-1011.11~22.04.1.1 amd64
linux-image-unsigned-6.2.0-1011-azure/jammy-updates,jammy-security 6.2.0-1011.11~22.04.1 amd64
linux-image-unsigned-6.2.0-1012-azure-fde/jammy-updates,jammy-security 6.2.0-1012.12~22.04.1.1 amd64
linux-image-unsigned-6.2.0-1012-azure/jammy-updates,jammy-security 6.2.0-1012.12~22.04.1 amd64
linux-image-unsigned-6.2.0-1014-azure-fde/jammy-updates,jammy-security 6.2.0-1014.14~22.04.1.1 amd64
linux-image-unsigned-6.2.0-1014-azure/jammy-updates,jammy-security 6.2.0-1014.14~22.04.1 amd64
linux-image-unsigned-6.2.0-1015-azure-fde/jammy-updates,jammy-security 6.2.0-1015.15~22.04.1.1 amd64
linux-image-unsigned-6.2.0-1015-azure/jammy-updates,jammy-security 6.2.0-1015.15~22.04.1 amd64
linux-image-unsigned-6.2.0-1016-azure-fde/jammy-updates,jammy-security 6.2.0-1016.16~22.04.1.1 amd64
linux-image-unsigned-6.2.0-1016-azure/jammy-updates,jammy-security 6.2.0-1016.16~22.04.1 amd64
linux-image-unsigned-6.2.0-1017-azure-fde/jammy-updates,jammy-security 6.2.0-1017.17~22.04.1.1 amd64
linux-image-unsigned-6.2.0-1017-azure/jammy-updates,jammy-security 6.2.0-1017.17~22.04.1 amd64
linux-image-unsigned-6.2.0-1018-azure-fde/jammy-updates,jammy-security 6.2.0-1018.18~22.04.1.1 amd64
linux-image-unsigned-6.2.0-1018-azure/jammy-updates,jammy-security 6.2.0-1018.18~22.04.1 amd64
linux-image-unsigned-6.5.0-1007-azure/jammy-updates,jammy-security 6.5.0-1007.7~22.04.1 amd64
linux-image-unsigned-6.5.0-1009-azure/jammy-updates,jammy-security 6.5.0-1009.9~22.04.1 amd64
linux-image-unsigned-6.5.0-1010-azure/jammy-updates 6.5.0-1010.10~22.04.1 amd64

```
This is just what I seem to do a lot from day to day... There "are" lots of other ways.

It is funny that on standard Linux Systems, "signed" is special and not the norm. But for Azure, they consider "unsigned" as special and not the norm(?)

---

### Post by ian-weisser on 2023-12-27
Let's see what the azure metapackage pulls in....

```
$ rmadison linux-image-azure | grep jammy
 linux-image-azure | 5.15.0.1003.4           | jammy           | amd64, arm64
 linux-image-azure | 6.2.0.1018.18~22.04.1   | jammy-security  | amd64, arm64
 linux-image-azure | 6.2.0.1018.18~22.04.1   | jammy-updates   | amd64, arm64
```

Unless you have removed that metapackage or mucked about with the apt sources, you simply apt update, apt upgrade, and then reboot into the new kernel.
For folks who leave Unattended Upgrades working, the apt update and apt upgrade should be done automatically already. You merely check them and then reboot.

---

