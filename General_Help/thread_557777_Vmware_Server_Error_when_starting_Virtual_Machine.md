---
title: "Vmware Server Error when starting Virtual Machine"
date: 2007-09-23
forum: General Help
---

### Post by snick512 on 2007-09-23
I've installed vmware successfully.. and made the virtual drive or w/e

when i go to click "power on" so i can install the other OS.. i get this message


"Unable to change virtual machine power state: The process exited with an error:
End of error message."

Any ideas?

---

### Post by cd1680 on 2007-10-01
i have the exact same problem. i also tried uninstalling v1.03 but it wont allow me. an error pops up saying cant find vmware-uninstall.pl. anyone know how to fix this?

---

### Post by distroman on 2007-10-01
I would have a look at the vmware forum.
[http://communities.vmware.com/search.jspa?resultTypes=BLOG_POST&resultTypes=DOCUMENT&resultTypes=MESSAGE&resultTypes=BLOG&resultTypes=COMMUNITY&peopleEnabled=true&q=Unable+to+change+virtual+machine+power+state](http://communities.vmware.com/search.jspa?resultTypes=BLOG_POST&resultTypes=DOCUMENT&resultTypes=MESSAGE&resultTypes=BLOG&resultTypes=COMMUNITY&peopleEnabled=true&q=Unable+to+change+virtual+machine+power+state)
If that don't help I would make a post there has helped me in the past.
> **cd1680 said:**
> i have the exact same problem. i also tried uninstalling v1.03 but it wont allow me. an error pops up saying cant find vmware-uninstall.pl. anyone know how to fix this?
```
sudo /usr/bin/vmware-uninstall.pl
```

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

gl

---

### Post by veloce on 2007-10-01
> **snick512 said:**
> I've installed vmware successfully.. and made the virtual drive or w/e

when i go to click "power on" so i can install the other OS.. i get this message


"Unable to change virtual machine power state: The process exited with an error:
End of error message."

Any ideas?

First thing to do is to turn on debugging for the vm.  This is in one of the options menus.  When you do this, you get a useful error message between the "with an error:" and "End of error message".

It can be a large number of things and you really need to know what the error is before you can start.

---

