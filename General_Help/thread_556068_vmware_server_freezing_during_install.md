---
title: "vmware server freezing during install"
date: 2007-09-20
forum: General Help
---

### Post by jabster on 2007-09-20
Hi.

I am trying to install vmware from the ubuntu commercial repositories and have run into a bit of a problem.

During the configuration within dpkg, the config gets to this point:
```
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
```
and hangs there forever (or at least 9+ hours).

However, I can start the server console and create a VM. I can't power it up as it asks for a serial number and tells me to run vmware-config.pl, which apparently isn't setup yet.

My main question is, how can I get back to using apt-get/dpkg again to install, update, etc, as I am stuck with this unconfigured package? Nothing in the man page jumped out at me as what to do next. I assume I need to force something, but what exactly? Just dpkg --force -r vmware-server?

I can live with removing the whole vmware thing.

Or, can someone tell me how to get around this freezing of the vmware config and get it to work correctly?

Thanks,
john

p.s. I'm running a fully updated feisty.

---

### Post by jabster on 2007-09-20
Well, while doing a different search, I found out how to remove vmware-server:
[http://ubuntuforums.org/showthread.php?t=426198](http://ubuntuforums.org/showthread.php?t=426198)

So this is good enough.

I'll play with it after gutsy maybe. Or alien the latest rpm here.

-john

---

