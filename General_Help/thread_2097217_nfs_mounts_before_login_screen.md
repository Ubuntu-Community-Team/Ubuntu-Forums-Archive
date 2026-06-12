---
title: "nfs mounts before login screen"
date: 2012-12-22
forum: General Help
---

### Post by jimbolaya on 2012-12-22
I run an NFS server at home that I use for home directories (among other things).  The problem I'm encountering is that gdm presents the login page before the home directory is mounted.

This results in the client using the local disk space if you log in too soon.  Is there a way to force the client to disallow or not show users who have NFS mounted home space until that share is mounted?

James

---

### Post by Derek Karpinski on 2012-12-23
If you're using /etc/fstab to mount your NFS shares, remove the lines from fstab, and use 'autofs' instead.

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

This will only mount shares when needed, and gets rid of the problem of shares not being ready when you boot.

Did I understand your problem correctly?

---

### Post by jimbolaya on 2012-12-30
> **Derek Karpinski said:**
> If you're using /etc/fstab to mount your NFS shares, remove the lines from fstab, and use 'autofs' instead.

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

This will only mount shares when needed, and gets rid of the problem of shares not being ready when you boot.

Did I understand your problem correctly?

Well, I don't necessarily want them unmounted (which autofs will do after some time).  

The problem is not that they aren't mounted.  The problem is that it takes some time for them to be mounted (even though the server is in the same room on the same network).  The login dialog is presented before the shares finished mounting, but if I wait a minute or two for the shares to be mounted, it all works fine.

My point is that the login dialog shouldn't be available until all the items in fstab are mounted that should be mounted with "mount -a".  Here are the appropriate lines in my fstab:

192.168.4.12:/home	/home	nfs	_netdev,auto  0  0
192.168.4.12:/media/md1	/media/md1	nfs	_netdev,auto  0  0

Before I didn't have my network card defined in /etc/network/interfaces, since I thought that might be an issue (network doesn't start until user logs in and uses network-manager to start it).  But that still doesn't completely solve the issue.

---

### Post by LewisTM on 2013-01-09
Hi,
I don't know if you solved your problem yet. 
From what I can read [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo#NFSv4_client"), the _netdev option is ignored for NFSv4 servers. I cannot verify this but you might want to add vers=3 to your fstab options, if your server allows NFSv3 style access. That should let Ubuntu wait for the server to be accessible before continuing the boot process. 

Hope this helps :)

---

