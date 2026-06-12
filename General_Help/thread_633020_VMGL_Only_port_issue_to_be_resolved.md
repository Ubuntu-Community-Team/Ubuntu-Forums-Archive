---
title: "VMGL: Only port issue to be resolved?"
date: 2007-12-06
forum: General Help
---

### Post by useResa on 2007-12-06
I have been trying to get VMGL working in VMware Server and I have the feeling I am pretty close ... however my knowledge stops at this point and therefore I hope someone can help me out.

Some basic info in advance:
Host: Ubuntu Gutsy Gibbon
Guest: Ubuntu Hardy Heron :)
VMware Server: Version 1.0.4 build-56528

What I have done so far is the following:
From the [VMGL site]("http://www.cs.toronto.edu/%7Eandreslc/xen-gl/") I have downloaded the rpm's for both the host and the guest. Using alien (including the --scripts option) converted both to deb files and installed them using dpkg.

After restarting I ran into the following error:
```
rdrijsen@hardy-vm:/etc$ glxgears
CR Error(hardy-vm:9238): Need to know glStub environment variable
rdrijsen@hardy-vm:/etc$ glxinfo
name of display: :0.0
CR Error(hardy-vm:9239): Need to know glStub environment variable
```Therefore I have edited the /etc/environment file in the guest and added the following line (as also suggested on the VMGL site).

However now I get the following error:
```
rdrijsen@hardy-vm:~$ glxgears
CR Error(hardy-vm:5520): Failed connect to hardy-vm:7001
rdrijsen@hardy-vm:~$ export GLSTUB=localhost:7001
rdrijsen@hardy-vm:~$ glxgears
CR Error(hardy-vm:5845): Failed connect to localhost:7001
```To me it seems that either the port is not open or I am using the wrong port. Is this a correct assumption?
If so, could anyone help me correct this error or
If not, can anyone help me out finding the correct cause of this error message.

[COLOR=Red]**EDIT:**[/COLOR]
Basically I like to see if I can get 3D acceleration working in a VM Guest.
One thing I did BEFORE installing VMGL was follow the instructions that are given for VMware Workstation (see [here]("http://www.vmware.com/support/ws55/doc/ws_vidsound_d3d_enabling_vm.html")).
This resulted in the fact that glxgears did work (see attachment), however GL did not work (for example SL did not start).
With VMGL SL no longer indicates that GL is not installed but provides the same error as above (cannot connect).

TIA

---

