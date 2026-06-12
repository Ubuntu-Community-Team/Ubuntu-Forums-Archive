---
title: "Landscape running custom scripts"
date: 2021-05-26
forum: General Help
---

### Post by vanilla-pod on 2021-05-26
Hi,  I have Landscape up and running fine but am struggling to get scripts to run on the clients.  Ideally I'd like to be able to run a script that reports back to the landscape server / myself whether iptables are enabled on the client device and what rules are in place etc.  Can this be done?  I'm wondering whether scripts can only run commands on the client and not report back to the Landscape server etc??  Thanks in advance

---

### Post by TheFu on 2021-05-26
I would use **ansible** for this need.
There is an ansible module for iptables: [https://docs.ansible.com/ansible/latest/collections/ansible/builtin/iptables_module.html#synopsis](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/iptables_module.html#synopsis)

---

