---
title: "VMware-Server: &quot;failed to lock file&quot; for VM on NFS drive"
date: 2007-05-06
forum: General Help
---

### Post by fbusse on 2007-05-06
I'm running the *VMware Server* on a host (Ubuntu Feisty with current updates). The virtual machine (VM) is on a server network drive and accessed over NFSv3. Upon start the *Server* complains:
```
Cannot open the disk '/mnt/export/tmp.vmdk' or one of the snapshot disks it depends on.
Reason: Failed to lock the file.
```

I've installed the *Server* using *apt-get* and the "vmware-server" package from canonical.com. The VM is a clone of a local VM from the host, which starts flawlessly. The only difference I notice so far is access via NFS.

[color=grey](The VM started and ran flawlessly even via NFS using the *Player* on another host on Edgy. From all other hosts on Edgy or on Feisty the *Player* complained upon startup: "Error while opening virtual machine /mnt/export/test.vmx: Failed to lock the file."[/color]

**NFS settings** are identical for all hosts, including options "nfsvers=3, nolock". The hosts are configured as NFS-clients only, thus having the "nfs-common" package installed (including lockd, statd, gssd and idmapd). **"dmesg | grep NFS"** shows no entry on the failing hosts.And I would like to stick to NFS (although I know about Samba).

The **hosts' "/etc/hosts"** have the server defined correctly, the **server's "/etc/hosts"** has none of the hosts defined at all. Access over NFS to other files (or even to the VM's configuration files using vim) shows no problems at all. Even tried to start the VMs as root with no visible effect.

My **firewall** is on the router, having no special settings for either of the hosts.

Any ideas?

ps: I posted the same question concerning the *Player* previously at  [vmware.com]("http://www.vmware.com/community/thread.jspa?messageID=594941"), [here](http://ubuntuforums.org/showthread.php?p=2472147) and at  [ubuntuusers.de]("http://forum.ubuntuusers.de/viewtopic.php?p=688890"), but finally got no solution. Obviously, neither the *Player*, nor the package on ubuntu.com was to be blamed for this error. (Crossposting at [vmware-forum.de](http://vmware-forum.de/viewtopic.php?p=34615) and at [ubuntuusers.de]("http://forum.ubuntuusers.de/topic/90528"))

---

### Post by etharis on 2008-03-27
I was running into the same problem, i deleted all the files in the VM directory except for the image file and the vmx file. When i went to open the vm again, it said "it looks like you have moved or copied this vm..." I selected "I moved it" even though it recommended "copied" and it worked fine and fixed my issues..

Hope that helps

Good luck

---

