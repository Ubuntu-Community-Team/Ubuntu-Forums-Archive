---
title: "No permissions"
date: 2013-04-09
forum: General Help
---

### Post by Deucalion29710 on 2013-04-09
**I  installed a Windoze 7 Virtualbox and now I can't get permissions for  anything.  Can't even mount my slave drive.  My main user account has no  root privelages (my only user account).  when I try chmod 440  /etc/sudoers it will not lock /etc/sudoers.  It appears that it may be  because it's now "read only".  When I appempt to execute "mount -o  remount, rw" that does not seem to work.  Lastly, usermod -a -G admin  username returns "usermod:group 'admin' does not exist"  any ideas on  fow to fix this so that I'm once again admin with read/write  permissions?**

---

### Post by efflandt on 2013-04-09
It is not clear if you installed Win7 as a client OS in Ubuntu and it messed up your Ubuntu host, or if you installed Ubuntu as a client in a Win7 host and are attempting to access physical partitions instead of virtual partitions. Not sure how to enable access to physical partitions, because I have only used VirtualBox to install and run other LInux versions from virtual drives on an Ubuntu host, and that all worked fine.

---

### Post by Deucalion29710 on 2013-04-09
> **efflandt said:**
> It is not clear if you installed Win7 as a client OS in Ubuntu and it messed up your Ubuntu host, or if you installed Ubuntu as a client in a Win7 host and are attempting to access physical partitions instead of virtual partitions. Not sure how to enable access to physical partitions, because I have only used VirtualBox to install and run other LInux versions from virtual drives on an Ubuntu host, and that all worked fine.


I installed Windows 7 as a guest OS just so that I could program a Harmony One.  Congruity/Concordence does not work for this model.  Anyway, it seems I had to add an extension pack for virtualbox and a virtualbox user in order to make my USB devices active on the guest OS.  That's when my user permissions changed.  If only us Linux users could just get some love from companies like Logitech and get software support all this could be avoided.  :mad:

---

