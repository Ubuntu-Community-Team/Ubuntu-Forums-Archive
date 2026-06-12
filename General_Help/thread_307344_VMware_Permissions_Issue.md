---
title: "VMware Permissions Issue"
date: 2006-11-26
forum: General Help
---

### Post by happy-and-lost on 2006-11-26
I'm using the latest VMware server, and am struggling with the permissions...

When I try to open a .vmx...
```

Unable to add virtual machine "/var/lib/vmware/Virtual Machines/Windows XP Professional/Windows XP Professional.vmx" to the inventory: No permission to perform this operation
```

](*,) 

(Yes, I do own rw permissions for these files)

---

### Post by NetworkGuy on 2006-11-26
My suggestion to you is to reconfigure VMware Server and have it look at your home directory for the virtual servers.  Makes it a lot easier for backups also.

---

### Post by happy-and-lost on 2006-11-26
Cheers, worked a charm :)

---

