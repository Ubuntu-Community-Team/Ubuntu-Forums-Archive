---
title: "Dynamic display resize in Ubuntu as VMWare Guest"
date: 2015-11-21
forum: General Help
---

### Post by knathraak on 2015-11-21
Hello,

I'm trying to get dynamic display resizing to work with Ubuntu 15.10 running as a guest on VMware Fusion 8.x. I can resize the display in the guest's settings but not dynamically by resizing the guest window. This is a fresh install. I've tried installing open-vm-tools both from apt and by building from source from github. I've also tried installing vmware-tools from VMware 8.

Is this a common problem? In older versions of Ubuntu and VMware Fusion, this worked fine.

Thanks.

---

### Post by knathraak on 2015-12-01
I resolved the issue by manually uninstalling VMware Fusion and all of its preferences per:
[VMware KB: Manually uninstalling VMware Fusion (1017838)]("http://kb.vmware.com/kb/1017838")
and then reinstalling.

If you have customized DHCP configuration for Fusion, you may want to back up /Library/Preferences/VMware Fusion/vmnet* first.

---

