---
title: "VMware problem in 7.10"
date: 2007-10-19
forum: General Help
---

### Post by Black Mage on 2007-10-19
Has anyone experienced a problem with running VMware in 7.10? When I try to power on a machine, it exits with an error.

```

Unable to change virtual machine power state: The process exited with an error:
End of error message.

```

---

### Post by bmorency on 2007-10-19
is it a fresh install of 7.10 or an upgrade? if it's an upgrade I wonder if you might have to reinstall vmware because it will install kernel modules for the current kernel.did you install vmware from the repos or from the files you got from the vmware.com? if it's form vmware.com this might be the problem.

---

### Post by Black Mage on 2007-10-19
No, I did an upgrade and I got the VMware through Ubuntu.

---

### Post by MegaSvensk on 2007-10-19
After installing Gutsy, VMware wouldn't run on my machine either. But I managed to fix it by running sudo /usr/bin/vmware-config.pl

Now it runs as well as it did before upgrading.

---

### Post by Black Mage on 2007-10-22
I tried that but go this

```

john@vmware-server:~$ sudo /usr/bin/vmware-config.pl
[sudo] password for john:
sudo: /usr/bin/vmware-config.pl: command not found


```

What else should I do? Or am I execting the command wrong?

---

### Post by veloce on 2007-10-22
There is a lot of mis-information going around about this. There were two ways to install vmware under fiesty: from the repos or manually using a download from the vmware site. 

If you installed from the repo then you won't be able to use your vms until the kernel related packages in the repos are updated. (Or you can uninstall the repo version and manually install.)

If you installed manually then the helpful instructions about running vmware-config.pl (and the any to any patch if required) will work.

BTW: The vmware console does currently allow you to run vms on other machines running vmware.

---

