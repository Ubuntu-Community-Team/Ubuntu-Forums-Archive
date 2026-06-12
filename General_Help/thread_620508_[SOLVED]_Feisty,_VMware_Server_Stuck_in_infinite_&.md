---
title: "[SOLVED] Feisty, VMware Server: Stuck in infinite &amp;quot;should upgrade / can't upgrade&amp;quot; lo"
date: 2007-11-22
forum: General Help
---

### Post by Phrawm48 on 2007-11-22
For Feisty and this puzzling information from Synaptic:

**Installed Version**
Version: 1.0.4-1feisty3
Size: 131 MB

**Latest Available Version**
Version: 1.0.4-1feisty3
Size: 131 MB
Download: 79.4 MB

I arrived at my current situation after struggling for some time to "unstick" an installation of VMware server I downloaded from the company's Web site.  As was the case for many others, the *vmware-uninstall.pl* script provided with that installation package seems incomplete, leaving one to locate and delete various directories, etc.

Having performed those steps, and after initially trying and failing to use Synaptic to install the "authorized" version of VMware Server, I selected the VMware Server components Synaptic believed to be installed and used **Mark for Complete Removal**.

I could then, as shown below, complete the installation process without receiving error messages, although evidently not without some sort of unreported error or errors:

> Preconfiguring packages ...
(Reading database ... 165432 files and directories currently installed.)
Preparing to replace vmware-server 1.0.4-1feisty3 (using .../vmware-server_1.0.4-1feisty3_i386.deb) ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done
Unpacking replacement vmware-server ...
Setting up vmware-server (1.0.4-1feisty3) ...
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
   Starting VMware virtual machines...                                 doneBut after completing this installation, Synaptic (and Update Notifier) report that an upgrade is available for the freshly installed VMware Server.  So in Synaptic I click **Apply** and walk through what appears to be an upgrade / installation process.  The process:[LIST]
[*]Includes the display of an End User Licensing Agreement panel, which I accept.
[*]Does not include, which is puzzling given the  *Download: 79.4 MB* information presented by Synaptic and listed above, any downloading...(?)[/LIST]After Synaptic goes through the motions of upgrading and refreshes itself, I look at VMware Server and see it still marked by Synaptic for upgrade.  Repeat into infinity...(?)

If I use *vmware -v *to get the version of the current instance I receive *1.0.4 build-56528*.

Per this forum, there seem to be multiple Feisty users having problems with uninstalling / installing VMware Server.  Since my problem seems slightly different than the ones reported in those threads, I'm creating this one.

So, can anyone please suggest how to get this infinite "should upgrade / can't upgrade" loop unstuck?

Cheers & thanks,
Ric
SFO

---

### Post by PoolSnoopy on 2007-11-23
Unfortunately I can't come up with a solution, but I wanted to join the club:

I'm stuck at version 1.0.4-1feisty2. Tried to upgrade twice, but my ubuntu can't get enough of upgrading vmware-server. :-)

---

### Post by blop on 2007-11-23
This is annoying...is there a way to tell Synaptic not to check that application for updates?

---

### Post by ppkkss on 2007-11-27
Same Here.  Hope someone can help.

---

### Post by Phrawm48 on 2007-11-27
Note that this issue has been reported as a bug per:
[B][URL="https://bugs.launchpad.net/ubuntu/+source/vmware-server/+bug/160683"]
vmware-server: Package requests recursive update[/URL][/B]

Per that bug's multi-comment narrative, this is evidently a non-trivial problem to resolve.

Cheers & hope this helps,
Ric
SFO

---

### Post by Phrawm48 on 2007-12-02
By the by, note that several bugs have been filed on this issue.  All these bugs have been marked as duplicates of the "master bug", 172275 per:

[vmware-server in feisty-commercial keeps getting reinstalled]("https://bugs.launchpad.net/soyuz/+bug/172275")

Cheers,
Ric
SFO

---

### Post by Phrawm48 on 2007-12-05
[FONT=Tahoma][SIZE=2]This problem is reported as fixed per:

[/SIZE][/FONT][FONT=Tahoma][SIZE=2][vmware-server in feisty-commercial keeps getting reinstalled]("https://bugs.launchpad.net/soyuz/+bug/172275")

Cheers & hope this helps,
Ric
SFO
[/SIZE][/FONT]

---

### Post by Phrawm48 on 2007-12-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/soyuz/+bug/172275](https://bugs.launchpad.net/soyuz/+bug/172275) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				[FONT=Tahoma][SIZE=2]This problem is reported as fixed per:

[/SIZE][/FONT][FONT=Tahoma][SIZE=2][vmware-server in feisty-commercial keeps getting reinstalled]("https://bugs.launchpad.net/soyuz/+bug/172275")

Cheers & hope this helps,
Ric
SFO
[/SIZE][/FONT]

---

