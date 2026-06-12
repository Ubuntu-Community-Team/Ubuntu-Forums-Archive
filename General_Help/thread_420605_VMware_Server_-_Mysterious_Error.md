---
title: "VMware Server - Mysterious Error"
date: 2007-04-23
forum: General Help
---

### Post by SniperSlap on 2007-04-23
After installing VMWare server by using the any-any (109) patch to compile my kernel modules, I am unable to power up any virtual machines.

I can configure them.  I can get them in the list, but as soon as I try to power on the machine, I get:

```
Unable to change virtual machine power state: The process exited with an error:
End of error message.
```

My VMWare log file has nothing conclusive to help either.  My research so far indicates a problem with vmmon, but the last piece of help says to use the 109 patch - which I have done...And I'm still experiencing this problem...

Anyone experiencing the same problem, or know of a solution?  

Thanks!

---

### Post by quad3d@work on 2007-04-23
Rerun vmware-config.pl again.

---

### Post by SniperSlap on 2007-04-24
I did that already.

Please, I am an experienced user: I have already done the obvious steps.

The any-any kit causes the script to be re-run anyway.

---

### Post by xamox on 2007-04-25
Getting the same problem as well.

---

### Post by vae on 2007-04-26
**vmware-config.pl did help** for me (prior to this I ran [FONT="Courier New"]vmware-any-any-update109/runme.pl[/FONT] and had the same problem).

For reference, here is an extract from error log file:
[FONT="Courier New"]Apr 26 18:39:44: vmx| ----------------------------------------
Apr 26 18:39:44: vmx| POST(no connection): Version mismatch with vmmon module: expecting 138.0, got 137.0.
Apr 26 18:39:44: vmx| You have an incorrect version of the `vmmon' kernel module.
Apr 26 18:39:44: vmx| Try reinstalling VMware Server.[/FONT]

---

### Post by Zuph on 2007-04-26
Is the VMWare on your feisty install newer than the one on your old install?  How are you VMDK files split?  Do you have any snapshots?  Have your VM directories moved (Did you back them up and then restore them)?

It may be a problem with disk consistency if you have snapshots or have moved the VMs.

A simple way to test this out is to create a new VM, but use the old VMDK files.

---

### Post by xamox on 2007-04-26
I have tried creating a new vmware. And have ran the vmware-config.pl. But neither seem to fix my problem.

---

### Post by xamox on 2007-05-01
someone posted this that made it to the frontpage of dig:
[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

---

