---
title: "Fstab NFS mount, not working on boot."
date: 2013-02-24
forum: General Help
---

### Post by Armann on 2013-02-24
Hi, I have a question about nfs in fstab.
It works fine and maps it right away if I run sudo mount -a
This is a pain since my home folder is on the nfs. :)

So any ideas what the issue could be ?

Thanks.

---

### Post by thermion on 2013-02-24
Please post your /etc/fstab

---

### Post by Armann on 2013-02-24
192.168.1.2:/volume1/X-Linux-Home /mnt/nfs/home/ nfs rw,hard,intr,rsize=8192,wsize=8192,timeo=14 0 0

Works fine when I manually run it...

---

### Post by prodigy_ on 2013-02-24
Add **_netdev** option and see if it helps.

---

### Post by Armann on 2013-02-24
Thanks for the help, that does point me in the right direction.
Still not working, I have a static ip so I'm not waiting for a dhcp.
Do you know what log I can look at to see what's happening ?
There is nothing in /var/log/syslog about this.

---

### Post by Armann on 2013-02-24
From looking at boot.log I would assume that the network was up
and running before it ran fstab.

/dev/sdb1: clean, 155923/697632 files, 896374/2789376 blocks
 * Starting mDNS/DNS-SD daemon                                           [ OK ]
 * Starting Uncomplicated firewall                                       [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting configure network device                                     [ OK ]
 * Starting configure network device                                     [ OK ]
 * Starting configure network device security                            [ OK ]
 * Starting Mount network filesystems                                    [ OK ]

---

### Post by prodigy_ on 2013-02-24
Is it NFSv4? If yes, you probably [won't be able to mount it from /etc/fstab](https://help.ubuntu.com/community/NFSv4Howto#NFSv4_Client). But I think it's still possible to automount at startup from rc.local or from a cron script running @reboot.

---

### Post by Armann on 2013-02-24
I don't know the NFS version, I'm guessing it's 4, it's a Synology DS212j box and I haven't found in the documentation or on their website what version of nfs it is.
I tried nfs4 in fstab instead of nfs and that didn't work, got a mount error.

I think the easy fix is rc.local :)

---

### Post by Armann on 2013-02-24
Well now it works but it takes 47 seconds to mount, then I can log in.
Guess I can thank that to _netdev, don't know why the delay is. :-|

---

### Post by Armann on 2013-02-24
For the people of the future... :popcorn:

What worked for me:
I had set a static ip address using Network Manager.
What I had to do was drop network manager all together,
don't need to delete it, if you add what I explain now
network manager does not manage that network adapter.

vim, vi, nano or whatever you use as your editor to open this file:
/etc/network/interfaces

Add this:

Change this so it applies your network.

auto eth0
iface eth0 inet static
address 192.168.1.101
gateway 192.168.1.254
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

Restart networking...

---

