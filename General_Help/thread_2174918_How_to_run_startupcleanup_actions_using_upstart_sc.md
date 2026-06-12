---
title: "How to run startup/cleanup actions using upstart script?"
date: 2013-09-16
forum: General Help
---

### Post by Konstantin_Boyandin on 2013-09-16
OS: Ubuntu 12.04 (64-bit).

Goal: create upstart script that will run one-time startup/cleanup actions without long-running process in between.

The script:

```

description     "test script"  
start on local-filesystems or runlevel [2345]
stop on runlevel [!2345] 

task 

exec /full/path/to/script.sh idle
pre-start exec /full/path/to/script.sh start
pre-stop exec /full/path/to/script.sh stop

```

The results:

```

$ start test
test stop/waiting

$ status test
test stop/waiting

$ stop test
stop: Unknown instance:

```

The script mentioned in stanzas is executed with 'start' and 'idle' parameters, but not with 'stop'.

Is it possible to solve the original task using upstart script, or shall I fall back to initscripts?

Thanks.

---

