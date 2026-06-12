---
title: "vmware-server permissions problem"
date: 2007-10-16
forum: General Help
---

### Post by J0ris on 2007-10-16
I have installed vmware-server in feisty. I started it up through the applications menu and selected local host. Then I wanted to change the default directory so that the virtual machines would be installed to a different partition (/home/....). Then I ran into permission problems that I haven't been able to resolve (see attached screenshot). From the help file it appeared that you have to be either root or a user with admin priviledges. The user I'm logged in as does have that. I also made sure that the folder permissions were set appropriately using chmod and chown, but I'm not sure what user vmware picks when you select local host nor do I know how to change that if such is required. It doesn't seem possible in the gui. Thanks for any help :)

---

### Post by ariek on 2007-10-16
Hi J0ris,

You could rerun the installation program, or change the config file **/etc/vmware/config**, and change the variable **vmdir**.

Arie

---

### Post by thierrybo on 2007-10-16
To administer VMware Server host (not a virtual machine), you need to be root.  Try running console as root to change vmware server settings.

---

### Post by J0ris on 2007-10-16
Worked like a charm. Thanks a lot, Arie!

---

