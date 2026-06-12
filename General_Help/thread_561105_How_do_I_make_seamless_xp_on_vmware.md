---
title: "How do I make seamless xp on vmware?"
date: 2007-09-27
forum: General Help
---

### Post by kris2pe on 2007-09-27
I'm using feisty and I want to configure my ubuntu to seamlessly work w/ xp using vmware!

---

### Post by danpre on 2007-09-27
> **kris2pe said:**
> I'm using feisty and I want to configure my ubuntu to seamlessly work w/ xp using vmware!

go to this very nice howto:
[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto]("http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto")

DANIeL

EDIT:
this one is easier:
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html")

---

### Post by bodhi.zazen on 2007-09-27
Set up vmware, then follow these instructions :

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

@danpre ~ The Ubuntu wiki has a very complete link on this as well ...

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

Yea, it is written with qemu , but basically, the way it works is that you use RDP to connect to a windows server and forward applications to ubuntu. Works with physical and virtual machines, qmeu, virtual box, and qemu ... :twisted:

---

