---
title: "esm-apps local repository"
date: 2023-10-24
forum: General Help
---

### Post by montheryas7821-1 on 2023-10-24
I am trying to create a focal-apps-updates and focal-infra-updates local repos instead of registering every single vm with pro attach <lic> this way we can keep VMs at the same patch level. 
I tried to create the local mirror with aptly but on getting hello package and nothing else.  I am also trying to avoid using landscape as we maintain our local mirrors using aptly and no need for another layer of complexity. 
Any idea if Ubuntu allow esm repos syncs locally?

---

### Post by TheFu on 2023-10-24
This reads like you are trying to get around Canonical's licensing.  Hacking a solution.  Don't think that's allowed in these forums. Perhaps if you clarify, an admin won't close this thread.

---

### Post by MAFoElffen on 2023-10-24
That is how I was reading that post. 

Because for commercial Ubuntu Pro subscriptions they say:
> 
[TABLE]
           [TR]
             [TH][/TH]
             [TH]Self-Support
(software only)[/TH]
             [TH]With Infra support
(24/7)[/TH]
             [TH]With full support 
(24/7)[/TH]
           [/TR]
                             [TR]
             [TD]Desktop
(workstation/year)[/TD]
             [TD]$25[/TD]
             [TD]–[/TD]
             [TD]$300[/TD]
           [/TR]
           [TR]
             [TD]Server with unlimited VMs*
(machine/year)[/TD]
             [TD]$500[/TD]
             [TD]$1,775[/TD]
             [TD]$3,400[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD]Notes[/TD]
[TD]* Any of: KVM | Qemu | Boch, VMWare ESXi, LXD | LXC, Xen, Hyper-V (WSL, Multipass), VirtualBox, z/VM, Docker. All Nodes in the cluster have to be subscribed to the service in order to benefit from the unlimited VM support[/TD]
[/TR]
[/TABLE]

So unlimited VMs per host is included in the host license, but they all have to be subscribed. That's how I read that. But then again, I am no one. I have no connection with Canonical. I am just another customer.

---

