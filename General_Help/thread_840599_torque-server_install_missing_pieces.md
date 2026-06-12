---
title: "torque-server install missing pieces?"
date: 2008-06-25
forum: General Help
---

### Post by retval on 2008-06-25
Anyone know of some kind of scheduler/PBS alternative thats in apt for torque-sever? Im not sure how I'm supposed to go about this in Ubuntu.

Thanks

> root@batch-server:~# apt-get install torque-server torque-scheduler torque-mom torque-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
torque-server is already the newest version.
torque-scheduler is already the newest version.
torque-mom is already the newest version.
torque-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up torque-mom (2.1.8+dfsg-0ubuntu1) ...
 * Starting Torque Mom: 
pbs_mom: No such file or directory (2) in chk_file_sec, Security violation with "/var/lib/torque/mom_priv/jobs"
invoke-rc.d: initscript torque-mom, action "start" failed.
dpkg: error processing torque-mom (--configure):
 subprocess post-installation script returned error exit status 3
Setting up torque-server (2.1.8+dfsg-0ubuntu1) ...
 * Starting Torque batch queue server: 
PBS_Server: No such file or directory (2) in chk_file_sec, Security violation with "/var/lib/torque/server_priv/jobs"
PBS_Server: No such file or directory (2) in chk_file_sec, Security violation with "/var/lib/torque/server_priv/queues/"
PBS_Server: No such file or directory (2) in chk_file_sec, Security violation with "/var/lib/torque/server_priv/accounting/"
PBS_Server: PBS_Server, pbsd_init failed
invoke-rc.d: initscript torque-server, action "start" failed.
dpkg: error processing torque-server (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 torque-mom
 torque-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@batch-server:~# 


---

### Post by agarzon on 2009-06-09
I am having the same problem, anyone has any input?

---

