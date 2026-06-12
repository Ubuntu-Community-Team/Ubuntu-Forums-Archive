---
title: "vmware-server: guest cannot communicate with host"
date: 2007-05-26
forum: General Help
---

### Post by Dromio on 2007-05-26
I've installed vmware-server from the repository with several guest machines (XP, FreeBSD, and Debian Linux) Each guest machine is set to run with bridged networking.  

Each machine connects to the network without issue and can communicate both ways with another machine on my LAN.  For example, I can SSH both to and from the FreeBSD VM and the other machines on my network.  

However I CANNOT communicate directly between the Host machine (Ubuntu Fiesty) and any of the virtual machines.  It looks like some weird quirk in the networking prevents it from routing properly.

Does anyone have any ideas on how to troubleshoot the problem?  I'd really prefer to use the repositories instead of having to fight with the tar.gz and compiling it every time Ubuntu upgrades their kernel.

---

### Post by Dromio on 2007-05-29
One bump to see if anyone has any suggestions.  Or at least tell me it's my problem and not common to everyone installing from the repository.

---

### Post by Megabird on 2007-05-31
I'm having the same problem here.  I'm able to ping the host from a client (WinXP, Windows 2000, WindowsNT4, Windows98, Windows Server 2003, and other linuxes) but no communication.  Setting up in NAS or Host mode works, with some limitations. In Bridged mode, no communications (except ping) goes thru.  I Had Workstation 6 beta installed previously and it worked correctly.

---

### Post by handband2 on 2007-06-02
Here are steps I used to get VMware-server from the Ubuntu repository working remotely.

I've attaced the pam_unix.so file and renamed it from the source files, downloaded from VMware's website.

Download file here:  [[COLOR="Red"]**pam_unix.vm.so**[/COLOR]]("http://ubuntuforums.org/attachment.php?attachmentid=34156&stc=1&d=1180818067")

```
$ tar zxvf pam_unix_vm.so.tar.gz
```

Move pam_unix_vm.so file to the location where your pam_unix.so file is:
```
$ sudo mv pam_unix_vm.so /lib/security/
```

Modify /etc/pam.d/vmware-authd so it will load the correct files:
```
$ sudo cp /etc/pam.d/vmware-authd /etc/pam.d/vmware-authd_backup
$ sudo gedit /etc/pam.d/vmware-authd
```
Change /etc/pam.d/vmwre-authd to the following:
```
#%PAM-1.0
auth sufficient pam_unix_vm.so shadow nullok
auth required pam_unix_auth.so shadow nullok
account sufficient pam_unix_vm.so
account required pam_unix_acct.so
```

I hope this helps.  If you need more information check out these sites:
[[COLOR="Red"]http://www.vmware.com/community/thread.jspa?messageID=636956[/COLOR]]("http://www.vmware.com/community/thread.jspa?messageID=636956")
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=426026&highlight=vmware+deb+package[/COLOR]]("http://ubuntuforums.org/showthread.php?t=426026&highlight=vmware+deb+package")

---

### Post by veloce on 2007-06-03
> **Dromio said:**
> I've installed vmware-server from the repository with several guest machines (XP, FreeBSD, and Debian Linux) Each guest machine is set to run with bridged networking.  

Each machine connects to the network without issue and can communicate both ways with another machine on my LAN.  For example, I can SSH both to and from the FreeBSD VM and the other machines on my network.  

However I CANNOT communicate directly between the Host machine (Ubuntu Fiesty) and any of the virtual machines.  It looks like some weird quirk in the networking prevents it from routing properly.

Does anyone have any ideas on how to troubleshoot the problem?  I'd really prefer to use the repositories instead of having to fight with the tar.gz and compiling it every time Ubuntu upgrades their kernel.

You could try adding host only networking to your vms.  This does involve your vms having two virtual network cards so you need to check that the routing works correctly.

Personally, I run a virtual firewall to control my vms access to the network and internet.  vms only have host only networking, the virtual firewall connects to the host only network and is also bridged. (I use IPCop + blockout traffic for the firewall, only uses 0.5Gb disk and 32Mb Ram.)

---

### Post by Megabird on 2007-06-04
> **veloce said:**
> You could try adding host only networking to your vms.  This does involve your vms having two virtual network cards so you need to check that the routing works correctly.


Sometimes, you cannot have more than one nic in your hardware.  I have to replicate user's PC for phone support, so the dual nic's won't work.  And I've got to test some Thin client app + PXE for deployment, so dial nic would do strange things.   I reverted to VMWare's tarball install with the any-any patch, witch works fine for now.  I'd prefer the repository based install, so I'll try again when the next update is out.

---

### Post by handband2 on 2007-06-04
Megabird,

It is possible to setup more than one nic.  I have three running on mine.  Just run the following
```
$ sudo /usr/bin/vmware-config-network.pl
```

and conncet your network cards different vmnets (The bridge is usually vmnet1 by default, so don't select that one).

---

### Post by veloce on 2007-06-04
> **Megabird said:**
> Sometimes, you cannot have more than one nic in your hardware.  I have to replicate user's PC for phone support, so the dual nic's won't work.  And I've got to test some Thin client app + PXE for deployment, so dial nic would do strange things.   I reverted to VMWare's tarball install with the any-any patch, witch works fine for now.  I'd prefer the repository based install, so I'll try again when the next update is out.

To replicate a user's PC for phone support, you'd want to use bridged networking, same for thin client.  The vms then act as if they are physical machines connected to the same network as the host - I assume that is what you are trying to replicate. (Provided that network is configured so that any new machine has the same treatment as existing machines.)

The only issue comes when you try to do "peer to peer" with the host.  I think vmware gets its routing confused from having host only and nat networks set up.  In this case, you should eliminate vmware's host only and nat networks by running:

vmware-config-network. 

The issue you are having is to do with the default virtual networks being installed.  The tarball install and the repository install have different defaults.  SO: it's not likely to change with the next update.

The only hassle with the repo version is that it reverts to default networking at each update.  The hassle with the tarball install, you've already experienced!

---

### Post by seamuso on 2007-06-04
> **Dromio said:**
> One bump to see if anyone has any suggestions.  Or at least tell me it's my problem and not common to everyone installing from the repository.



When I used the repositories for install, I had the same problem .. I used a different set of install instructions and everything worked without issue.

[http://ubuntuforums.org/showpost.php?p=2712345&postcount=15](http://ubuntuforums.org/showpost.php?p=2712345&postcount=15)

my current (this post reminded me to rerun vmware-config.pl)

```
The configuration of VMware Server 1.0.3 build-44356 for Linux for this running
kernel completed successfully.

seamuso@bluebuntu:~$ uname -a
Linux bluebuntu 2.6.21.3-ck2 #1 SMP PREEMPT Sun Jun 3 22:05:47 MDT 2007 i686 GNU/Linux

```

---

