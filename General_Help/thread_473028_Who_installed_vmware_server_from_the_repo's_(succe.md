---
title: "Who installed vmware server from the repo's (successfully)"
date: 2007-06-13
forum: General Help
---

### Post by eentonig on 2007-06-13
I just installed vmware-server from the repositories, but it seems I can't run any VM.

They all fail to boot. Did anybody succeed in getting a working vmware-server this way?

---

### Post by AndyCooll on 2007-06-13
Are you sure you actually installed VMware Server itself, I didn't think it was available in the repositories. Whenever I've installed it I've had to get it from the VMware website. 

What I can see _is_ in the repositories are the VMware Server kernel modules, however these aren't the actual VMware Server app. So ...which repo did you find Server in?

:cool:

---

### Post by eentonig on 2007-06-13
Canonical commercial repo.

> sudo apt-get install vwmare-server vmware-server-kernel-modules vmware-tools-kernel-modules

The install works fine. But running the VM's is a problem

---

### Post by eentonig on 2007-06-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/120325](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/120325) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I created an bug report regarding this.

---

### Post by zvacet on 2007-06-14
Look at synaptic just to be sure you installed all you need.I did it that way.Just from synaptic and it is work.

---

### Post by eentonig on 2007-06-14
I already did that. 

I installed the server and the server-kernel-modules. What else was needed? And why wasn't it included as a dependancy?

By the way. It seems like it has a problem finding some modules. I see a warning regarding 'vmmon'

---

### Post by eentonig on 2007-06-14
Ok, found a solution/work around

download tthe vmware-any-any-update patch from
[http://knihovny.cvut.cz/ftp/pub/vmware/](http://knihovny.cvut.cz/ftp/pub/vmware/) and run "runme.pl" 

Vmware works afterwards.

---

