---
title: "VMware-Player: &quot;failed to lock file&quot; for VM on NFS drive"
date: 2007-04-18
forum: General Help
---

### Post by fbusse on 2007-04-18
I'm running the VMware Player on some hosts (all Ubuntu Edgy with current updates). The virtual machines (VMs) are on a server network drive and accessed over NFSv3. (Each host is indeed trying to access the same virtual machine, but not at the same time, of course).

The VMs start and run with no problems on a first host, while on a second the player complains on startup: ```
Error while opening virtual machine /mnt/export/test.vmx: Failed to lock the file.
```

I've installed the Player using apt-get, taking "vmware-player" from the repo's at ubuntu.com. And I would like to stick to both the Player (although I know about the Server), to that repo (although I know about the "original" files being available at vmware.com) and to NFS (although I know about Samba).

**NFS settings** are identical for all hosts, including options "nfsvers=3, nolock". The hosts are configured as NFS-clients only, thus having the "nfs-common" package installed (including lockd, statd, gssd and idmapd). **"dmesg | grep NFS"** shows no entry on the failing hosts.

The **hosts' "/etc/hosts"** have the server defined correctly, the **server's "/etc/hosts"** has none of the hosts defined at all. Access over NFS to other files (or even to the VM's configuration files using vim) shows no problems at all. Even tried to start the VMs as root with no visible effect.

My **firewall** is on the router, having no special settings for either of the hosts.

Any ideas? In particular, it might be helpful to increase verbosity of the Player in order to get to know what exactly it is trying to do.

ps: I had posted the same [at vmware.com in February]("http://www.vmware.com/community/thread.jspa?messageID=594941"), but finally got no solution. ([crossposting at ubuntuusers.de]("http://forum.ubuntuusers.de/viewtopic.php?p=688890"))

---

### Post by vlad_x2 on 2007-04-18
I got the same problem with the player some time ago. Try to delete the lock files after closing the VM. It worked for me ;).

---

### Post by fbusse on 2007-04-18
> **vlad_x2 said:**
> Try to delete the lock files after closing the VM.
I would be happy if it were that simple: There is no lock file!

But thx for thinking about my question! ;-)

---

### Post by fbusse on 2007-04-22
Addendum: Updating to Feisty made it even worse - Now there is no machine left with access to the NFS drive. :-(

---

### Post by optotron on 2007-04-25
This error message can appear if you've got no space left on the devices from which you load the vmware image . In that case, making some free space will make it work again!

---

### Post by fbusse on 2007-04-30
> **optotron said:**
> This error message can appear if you've got no space left on the devices from which you load the vmware image . In that case, making some free space will make it work again!
@optotron: The related drive actually has 20 Gig free. Should be sufficient for a lock file... ;-)

---

### Post by maitrebart on 2008-01-28
I got the same problem as yours. If you found any solution, let me know!
Thanks.

---

### Post by Robstarusa on 2008-02-12
I also have the same problem.....Anyone?

Rob

---

### Post by discodan on 2008-02-24
For me this was a permissions issue.

Verify that the user you are logged in with has permissions to the virutal machines folder.

-disco-

---

### Post by kdmit on 2008-06-18
GREAT!!!!!
I had the same problem.
SOLUTION:
change the permission to FOLDER that contains the Virtual Machine.

:D:D:D

---

