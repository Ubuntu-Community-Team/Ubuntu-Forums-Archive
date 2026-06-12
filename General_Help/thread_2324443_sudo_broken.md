---
title: "sudo broken"
date: 2016-05-13
forum: General Help
---

### Post by jamesisin on 2016-05-13
I have broken sudo.  I can't see a path to fixing it.

I have a domain joined machine running 16.04 64 bit Ubuntu.  I was attempting to add a user and a couple of domain groups to the sudoers list by adding a file under /etc/sudoers.d/.  I was able to do just that, but apparently sudo does not like my syntax.

```
sudo ls
>>> /etc/sudoers.d/DomainAdminRights: syntax error near line 3 <<<
sudo: parse error in  near line 3
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin

```

My file is pretty simple.

```
cat /etc/sudoers.d/DomainAdminRights 
# Added 20160513 for domain level admin rights
particularusername ALL=(ALL:ALL) ALL
%"Domain Admins" ALL=(ALL:ALL) ALL
%spacelessgroupname ALL=(ALL:ALL) ALL

```

I tried using a ^ in lieu of a space but that was not working; so I tried quoting the group name.  This is what caused the problem.  (Sudo hates quotes?  I don't know.)

No one can sudo, so I can't remove the file.  The disk is encrypted, so I can't just mount it with something else.

A little help?

---

### Post by jamesisin on 2016-05-13
Got it...

[http://jamesisin.com/a_high-tech_blech/index.php/2011/12/attach-ubuntu-to-windows-domain-via-active-directory-sudo/](http://jamesisin.com/a_high-tech_blech/index.php/2011/12/attach-ubuntu-to-windows-domain-via-active-directory-sudo/)

"you can always use pkexec visudo -f /etc/sudoers to fix it"

---

