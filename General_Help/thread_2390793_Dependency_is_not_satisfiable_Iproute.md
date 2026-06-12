---
title: "Dependency is not satisfiable: Iproute"
date: 2018-05-02
forum: General Help
---

### Post by heroquestelf on 2018-05-02
First off, I am running a Dell Experion with a 4x Intel Core i5-4460 3.2    GHz  processor with 8088MB of RAM. I am running Ubuntu MATE and have recently updated to the new LTS, 18.0

When I went to reinstall my VPN software, it gave me the following error "Dependency not Satisfiable: iproute".

Any ideas on a workaround?

---

### Post by SeijiSensei on 2018-05-02
Try "sudo apt install iproute2" then run the VPN installer again.

---

### Post by heroquestelf on 2018-05-02
I actually tried that already, and what I got was

> 
iproute2 is already the newest version (4.15.0-2ubuntu1).

---

### Post by SeijiSensei on 2018-05-02
if this software comes from your VPN provider, you probably need to talk to them. People here can help with things like OpenVPN, but that doesn't sound like the source of this problem.  If you are using OpenVPN, can you show us the .conf file and any scripts that are invoked along the way?

---

