---
title: "NFS Stopped Working For No Reason"
date: 2007-01-24
forum: General Help
---

### Post by mtdewulf on 2007-01-24
I have a server running dapper with a raid 5 volume (/dev/md0/) that I have set up to be shared via nfs over the network.

I have a client computer also running dapper that mounts this volume in fstab with the line:
192.168.0.12:/mnt/warehouse /home/mtdewulf/warehouse nfs rw 0  0

Up until last night everything worked fine.  Then, for apparently no reason, I noticed the contents of the folder were no longer showing up.  I tried a "sudo mount -a" but I get the following error:

mount to NFS server '192.168.0.12' failed.

The only thing that I was doing differently on the server that I can think of was running Azureus.  However, once I had an error mounting NFS, i decided to restart the computer (at this point, I also installed a bunch of updates including the newest kernel - the server has not been down for over 2 months).

I also restarted the client and the router connecting the two.  However, I still get the same error message.  

I have no idea what is wrong because as far as I know, nothing changed on the server when the error occured (wasn't installing anything, etc.)

I should note that I am still able to ssh, sftp, vnc, and sshfs into the server.  It only seems that NFS is no longer working.

Has anyone had this problem or does anyone know what is going on?  Any help would be very appreciated!

Thanks,
Mike

---

### Post by matthewstory on 2007-01-24
are you running the user server or the kernel server?  Do you have a firewall (maybe iptables) running on the server?  Is the RAID device still mounting properly to the filesystem?  What do your export, hosts.allow and hosts.deny files look like?  Does your server have a static IP?  Are you running an NFS client version of portmapper that works with the version of NFS server you have running on your server?  Do you have a stale NFS mount on the client?  Have you tried sudo umount --force on the client and then sudo mount -a?  

Sorry a lot of questions, but NFS is a complex animal.

---

### Post by mtdewulf on 2007-01-24
-I am running the kernel server.

-No firewall on the server.

-Raid drive is still mounted properly.

-hosts.allow hosts.deny and export have not changed since nfs was working.

-Server is a static IP.

-NFS client and server versions match.

Is there something Azureus could have done to mess up my network settings for the server?

---

### Post by thk on 2007-01-24
I find this is invariably caused by the portmap daemon crashing. See if restarting portmap on the server and/or clients fixes the problem.

---

### Post by mtdewulf on 2007-01-24
I tried restarting portmap with no luck.  I also have rebooted the server.  I did some more investigating and found that when I try to connect from the client (192.168.0.11), I get the following error messages in /var/log/syslog:

Jan 24 22:36:11 localhost portmap[6684]: connect from 192.168.0.1 to getport(nfs): request from unauthorized host
Jan 24 22:36:11 localhost portmap[6685]: connect from 192.168.0.1 to getport(nfs): request from unauthorized host

This is really odd since 192.168.0.1 is the address of the router itself.  I don't understand how requests from 192.168.0.11 can be showing up as connections from 192.168.0.1???

---

### Post by mtdewulf on 2007-01-25
Any ideas?  I also noticed that my connection between the client and server is now slow.  I.E. it used to be around 1.4MB (wireless) transfers and now it is at 100KB.  Is this a sign that my router is acting up?  I should note that I'm using ddwrt.

---

### Post by matthewstory on 2007-01-26
did you change your router config with port forwarding to work for azureus?  It might explain why it seems to be coming from the router.

---

### Post by mtdewulf on 2007-01-26
I did, but that was only for the azureus port.  I don't know why that would interfere with the NFS ports.

---

### Post by kosmic on 2007-01-26
Just for curiosity what ports did you forward for azureus ?? Maybe it is in the range of the ports use by portmap

Look careful to the error :

Jan 24 22:36:11 localhost portmap[**6684**]: connect from 192.168.0.1 to getport(nfs): request from unauthorized host

Arfe you sure that your router is not forwarding that port to azureus ??

---

