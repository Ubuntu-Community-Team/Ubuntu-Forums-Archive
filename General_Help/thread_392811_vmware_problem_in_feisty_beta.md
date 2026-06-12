---
title: "vmware problem in feisty beta"
date: 2007-03-25
forum: General Help
---

### Post by benner on 2007-03-25
i just installed vmware workstation 6 beta on my new ubuntu feisty 64 system. it installed fine. it opens fine. it even created a new virtual machine without any problems. when i tried to open an existing virtual machine (that worked fine yesterday on edgy) i got the following error message.

"Unable to change virtual machine power state: Failed to connect to peer process."

so i figured maybe my virtual machine was the problem so i created a new one. no problem. when i tried to open it, same message:

"Unable to change virtual machine power state: Failed to connect to peer process."

 thanks in advance for any suggestions...

---

### Post by benner on 2007-03-25
no responses yet?  is anyone else having the same problem?

---

### Post by zvacet on 2007-03-25
I´m not sure,but maybe to reconfigure it?Just an idea not solution.

---

### Post by benner on 2007-03-25
i did.  twice.  no go.

---

### Post by vlad_x2 on 2007-03-31
The problem seems to be the vmmon kernel module. I ran vmware from the terminal and got a couple of error windows that said that the vmmon kernel module is older than expected and it could not connect to it.

If I run as a normal user in terminal this is what I get:
vlad@vlad-feisty:~$ vmware


VMware Workstation Error:
VMware Workstation must be set-UID root, "/usr/lib/vmware/bin/vmware-vmx" is not.  Are you running /usr/lib/vmware/bin/vmware-vmx from its distribution directory?  That copy of the program is not set-UID root.

Press "Enter" to continue...

As root this is what I get:

An error window saying:
"Version mismatch with vmmon module: expecting 161.0, got 138.0.
You have an incorrect version of the `vmmon' kernel module.
Try reinstalling VMware Workstation."

"Failed to initialize monitor device."

"Unable to change virtual machine power state: Cannot find a valid peer process to connect to."

"Failed to reply to the dialog: Pipe: Read failed"

I had installed vmware server before that, maybe the sources for the kernel module were not updated and vmware-config.pl builds the older vmmon. I will try to completely remove vmware and install again. I'll post again after reinstalling. :(
I run kernel 2.6.20-13-generic (32 bit).

---

### Post by vlad_x2 on 2007-03-31
I reinstalled, but no luck. The vmmon module seems to be outdated. :(

---

### Post by vlad_x2 on 2007-03-31
Phew... I finally got it working.
I reinstalled from the tar (I installed by converting the rpm to deb with alien before) and it worked like a charm. :)

---

