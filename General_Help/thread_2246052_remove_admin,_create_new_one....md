---
title: "remove admin, create new one..."
date: 2014-09-28
forum: General Help
---

### Post by DeMartini on 2014-09-28
I am selling my laptop running 14.04, the buyer is excited about ubuntu and wants to keep the OS. I simply want to remove me and add him as admin, keeping all the settings i currently have. This OS is set up perfectly, and i'd love to avoid having to start over, rather just slide him in and get me off. Thanks in advance.

---

### Post by TheFu on 2014-09-28
/etc/passwd
/etc/shadow
/etc/sudoers
and perhaps
/etc/samba/smb.conf and the smbpasswd file.

It is all about the userid, groups and sudoers.  Be careful about the order you edit those files and do the sudoers last. Best to add the new userid first, test, then remove your old userid. I'd reboot as part of the testing - BEFORE removing your userid from these files.

---

### Post by Lars Noodén on 2014-09-28
In 14.04, the 'admin' type account defaults to these groups: adm, cdrom, sudo, dip, plugdev, lpadmin, bluetooth, and sambashare
If you add the new user to those groups, they will have full rights to the machine and you can then remove your user from these groups.  You can use [usermod](http://manpages.ubuntu.com/manpages/trusty/en/man8/usermod.8.html) or edit (oh so carefully) the files mentioned above by TheFu.

Then once you have tested that the new account has full rights, you can remove your user from adm and sudo and maybe the others though you might want to stay in bluetooth and cdrom at least if you use those.

---

