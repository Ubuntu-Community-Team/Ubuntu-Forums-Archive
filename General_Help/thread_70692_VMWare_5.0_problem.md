---
title: "VMWare 5.0 problem"
date: 2005-09-30
forum: General Help
---

### Post by Adam Lee on 2005-09-30
> *** VMware Workstation internal monitor error (bug 9297) ***

The guest operating system you are running is using the Physical Address Extension (PAE) processor option.  For more information about
running PAE-enabled guest operating systems, please consult [http://www.vmware.com/info?id=28](http://www.vmware.com/info?id=28)

This is what I got when I tried to install Windows XP

Thx in advance.

---

### Post by mlord on 2005-10-02
Add this line to your winxp machine's .vmx file:

paevm = "TRUE"

---

