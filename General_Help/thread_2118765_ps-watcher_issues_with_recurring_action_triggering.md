---
title: "ps-watcher: issues with recurring action triggering"
date: 2013-02-22
forum: General Help
---

### Post by Sambo_ on 2013-02-22
**OS:** Ubuntu 12.04 LTS
**App:** ps-watcher v1.08-2
**Linux Experience:** 3 months
**General IT Experience:** 20 years :D

Hi everyone,

I am attempting to setup ps-watcher to monitor a process and alert me once if it stops.  I have configured ps-watcher to monitor the system every 60 seconds and alert me when my target process stop and that all works fine, the issue I'm having is that it repeatedly alerts me every minute.  How can I set this up so it only alerts me once, until the process is restarted and then stops again?

Here is my ps-watcher config file:

```

[process_name]
occurs = none
action = echo "process_name has stopped"

```Any assistance greatly appreciated!

---

