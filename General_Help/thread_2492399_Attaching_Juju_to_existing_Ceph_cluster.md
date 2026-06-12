---
title: "Attaching Juju to existing Ceph cluster"
date: 2023-11-09
forum: General Help
---

### Post by swampcritter on 2023-11-09
I stood up a disposable ceph cluster under anested VMware ESXi host (running under VMwareWorkstation) so I could learn the in's and out's ofhow Ceph functions. I stood up a single node Cephmonitor (Ubuntu 22.04 Desktop and 3x ceph OSD nodes (allocated with 100GB of space via /dev/sdb), all running Ubuntu 22.04 server. I followed a 3rd party steps on setting up a Ceph cluster using Ansible ([https://computingforgeeks.com/install-ceph-storage-cluster-on-ubuntu-linux-servers/](https://computingforgeeks.com/install-ceph-storage-cluster-on-ubuntu-linux-servers/)). The cluster (i.e., monitors and ceph nodes) is up and running fine.

My question is I would like to use Juju to connect to said existing Ceph cluster so that I can use Juju to help manage it. I thought that since Juju acts more like an orchestrator, that you could just add already deployed instances to its database and then manage it from there. Juju has such a large learning curve that I why I found it was easier just to stand up a ceph cluster via an automation tool like Ansible (I've seen versions of doing it with Chef as well).

Is there any how-to document or steps available on how to do this? 

I can install the juju client on either a standalone Ubuntu server or one (or all) of the monitor nodes.

---

