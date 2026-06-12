---
title: "VMware wont work on Dapper"
date: 2006-10-31
forum: General Help
---

### Post by turkenator on 2006-10-31
hi 
Im running Kubuntu Dapper im having some trouble getting Vmware to work 
i installed the Rpm installation file via alien and  when i try to run vmware on konsole 
montana@montana:~$ vmware
/usr/bin/vmware: line 85: /etc/vmware/locations: No such file or directory
/usr/bin/vmware: line 177: /lib/wrapper-gtk24.sh: No such file or directory
/usr/bin/vmware: line 177: exec: /lib/wrapper-gtk24.sh: cannot execute: No such file or directory
any help will be appriciated if there is precompiled packages for ubuntu a link would also help thanks in advance

---

### Post by firetux on 2006-10-31
Thats' not the way you should install it. Just use the tar.gz, It's really easy. Here are plenty of howto's too.

---

### Post by turkenator on 2006-10-31
ok thanks ill try it btw how do u uninstall programs installed with alien?

---

### Post by firetux on 2006-10-31
```
sudo apt-get remove *packagename*
```

---

