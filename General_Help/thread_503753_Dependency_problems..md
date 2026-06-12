---
title: "Dependency problems."
date: 2007-07-18
forum: General Help
---

### Post by JesterDev on 2007-07-18
A few days ago I was installing some software via the update manager and ubuntu froze on me near the end. Now every time I install something I get this error:

```

E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured

```

And in the terminal:
```

Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured

```

I´ve tried apt-get update, upgrade etc and nothing seems to fix this. Any ideas?

---

### Post by JesterDev on 2007-07-18
No thoughts? Ideas?

---

### Post by JesterDev on 2007-07-20
Is there anyway for me to remove this broken programs? Perhaps they are stored somewhere when I can just delete them. Then again perhaps they are just partially installed,in which case they will just cause more problems.

---

### Post by Rebeca on 2007-07-20
Have you tried:

```
sudo apt-get -f install
```

?

---

### Post by JesterDev on 2007-07-20
Yes I sure did. And I get:

```

Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Other then that the results are still the same. 

Makes me wonder if my updates are being installed correctly also. But so far no major issues have arisen from this.

---

### Post by JesterDev on 2007-07-20
Well I´m at a loss here. I´ve tried just about everything I can think of, including attempting to install them again. Still no go. I´m thinking I may have to ask elsewhere. :confused:

---

### Post by frenchcr on 2007-07-20
I have exactly the same problem:

After i install new packages in synaptic (everthing installs as normal)...i get the following errors once synaptics' finished: 

E: clvm: subprocess post-installation script returned error exit status 3 
E: redhat-cluster-suite: dependency problems - leaving unconfigured

The problem began when i tried to install redhat-cluster-suite in the usual manner.

Im :confused: tbh

Someone, somewhere please.

---

### Post by frenchcr on 2007-07-20
Ive reduced the warnings by reinstalling cman...now i just get:

E: clvm: subprocess post-installation script returned error exit status 3


There has been a bug report and it seems to be the same problem as ours...

[https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/86087](https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/86087)

..but i am out my depth, can someone explain whats wrong.

---

### Post by JesterDev on 2007-07-21
Well I guess there´s not much else to do but wait for a fix. Lots of others seem to be having the same issues. After reinstalling like you did, I now get the same error as you minis the red hat issue.

---

