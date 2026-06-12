---
title: "Uninstalling software HOWTO"
date: 2007-06-03
forum: General Help
---

### Post by nami on 2007-06-03
How do you uninstall software?  I installed vmware server using this guide [http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto).

Hows the best way to uninstall it completely?

---

### Post by kdarkentity on 2007-06-03
well... i would say to go to synaptic and remove any packages you installed to use it and then look in your home folder for any files that may be associated with it and delete those ...i'm not sure if this will help or not as i dont even know what vmware is ...i have heard of it tho

---

### Post by rbmorse on 2007-06-03
> **nami said:**
> How do you uninstall software?  I installed vmware server using this guide [http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto).

Hows the best way to uninstall it completely?

/usr/bin/vmware-uninstal.pl

---

### Post by nami on 2007-06-03
> **kdarkentity said:**
> well... i would say to go to synaptic and remove any packages you installed to use it and then look in your home folder for any files that may be associated with it and delete those ...i'm not sure if this will help or not as i dont even know what vmware is ...i have heard of it tho

it's an amazing bit of software, don't know what i would do without it.

> **rbmorse said:**
> /usr/bin/vmware-uninstal.pl

that worked thanks! :D

---

### Post by mkoehler on 2007-06-03
In the future, you can either go to synaptic, or type ```
apt-get remove <program name>
```

---

### Post by ubuntu_amatuer on 2007-12-29
Will the apt-get uninstall uninstall the softwares dependencies or other packages it installed ? or just the software only.

---

