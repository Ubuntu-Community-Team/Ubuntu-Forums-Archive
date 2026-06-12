---
title: "NFS: still not working"
date: 2021-02-03
forum: General Help
---

### Post by Old Jimma on 2021-02-03
HI Community:

NFS is still not working. Here are the commands I used:


**HOST**
[COLOR="#FF0000"]
 sudo apt update
$ sudo apt install nfs-kernel-server
$ sudo mkdir /mnt/nfs/joecool -p
$ sudo chown nobody:nogroup /mnt/nfs/joecool

$ sudo gedit /etc/exports

/mnt/nfs/joecool     192.168.4.23/22(ro,sync,no_subtree_check)
/home               	 192.168.4.23/22 (ro,sync,no_root_squash,no_subtree_check)
$ sudo systemctl restart nfs-kernel-server

$ sudo ufw allow from 192.168.4.22 to any port nfs
$ sudo ufw allow from 192.168.4.23 to any port nfs
$ sudo ufw enable
$ sudo ufw status

 $ sudo ufw numbered
Status: active

To                         Action      From
--                         ------      ----
2049                       ALLOW       192.168.4.23              
2049                       ALLOW       192.168.4.22  

[/COLOR]


**CLIENT**
[COLOR="#FF0000"]
$ sudo apt update
$ sudo apt install nfs-common
$ # CREATE THE MOUNT POINTS
$ sudo mkdir -p /nfs/joecool
$ sudo mkdir -p /nfs/home

$ sudo gedit /etc/fstab

192.168.106:/nfs/joecool    /nfs/joecool   nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0
192.168.106:/home                     /nfs/home            nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0

[/COLOR]

What did I do wrong?

Old Jimma

---

### Post by dinkidonk on 2021-02-03
Are you sure that "/22" is what you want? Try to remove it from these lines:

```
/mnt/nfs/joecool     192.168.4.23/22(ro,sync,no_subtree_check)
/home                    192.168.4.23/22 (ro,sync,no_root_squash,no_subtree_check)
```

The number after the "/" means how many bits should match in the IP-address, 22 bits does not even cover the first three bytes (192.168.*) and the last byte (23) is ignored.

EDIT: Oh, and in your client, you have specified an invalid ip (192.168.106).

---

### Post by HermanAB on 2021-02-03
Did you start the NFS server?

You can check whether it is running with ps or top and check whether it responds with telnet.

This is supposed to start nfsd on the server:
$ sudo systemctl restart nfs-kernel-server

See if it is running:
$ ps -e | grep nfsd

See if it is responding:
$ telnet localhost  2049
You should get some response message, then quit telnet again.

Also test from the client machine:
$ telnet serveripaddress 2049

Only once you are SURE that the server is working and that you can reach it from the client machine, then you can bother with the client setup.

---

### Post by dinkidonk on 2021-02-03
Btw., if you want to export to both the IP's "192.168.4.22" and "192.168.4.23", it must be declared as:

```
/path/to/folder 192.168.4.22(options for 22) 192.168.4.23(options for 23)
```

The "/" defines a [CIDR notation (subnet mask)](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing) - do not use this if you do not know what it does since it may become a security risk.

The client must have the full IP address of the server.

---

### Post by Old Jimma on 2021-02-03
Thanks to **dinidonk** an **HermanAB** for their replies and guidance.

In respone to one of B]HermanAB's[/B] comments, I explored if the NFS server was running: **it was not running.**

I looked at my /[COLOR="#FF0000"]etc/exports[/COLOR] file and found that it include a line that said something like [COLOR="#FF0000"]sudo ufw allow from 192.168.4.22 to any port nfs[/COLOR]

After making that correction,  followed the procedure ABHerman suggested and found that the NFS server was running.

I've made the other changes requested, but the NFS is still not working here are my  /etc/exports and /etc fstab files

Also, I confirm that the IP address of my server is: **192.168.4.23**

I confirm that the IP address of my client is: **192.168.4.23**


**/etc/exports**

> [COLOR="#FF0000"]
## WIFI kitchen Lenovo computer
/mnt/nfs/joecool        192.168.4.23(ro,sync,no_subtree_check)
/home               	 192.168.4.23 (ro,sync,no_root_squash,no_subtree_check)
[/COLOR]


**/etc/fstab**

> 

[COLOR="#FF0000"]192.168.106:/nfs/joecool    /nfs/joecool   nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0
192.168.106:/home                     /nfs/home            nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0[/COLOR]



Thank you for your comments, What else can be corrected in these files?

**THANK YOU SO MUCH!!**

Old Jimma

---

### Post by HermanAB on 2021-02-03
I would first test the nfsd and client on the server machine itself.  Only once it is definitely working there on one machine, will I move over to the second client machine.  This is to avoid getting bogged down with network issues while sorting out the server. Divide and conquer.

---

### Post by dinkidonk on 2021-02-03
The fstab is wrong, "192.168.106" is not a valid IP address. On the server, run the command "hostname -I" to get the full IP address (eg. 192.168.106**.10**) and use that in fstab on the client:

```
192.168.106**.10**:/nfs/joecool    /nfs/joecool   nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0
192.168.106**.10**:/home                     /nfs/home            nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0
```

Also mind that "/nfs/joecool" is not exported on the server, do you mean "**/mnt**/nfs/joecool"?

---

### Post by TheFu on 2021-02-03
/mnt/nfs/joecool actually has storage on the server?
**showmount -e** run that on the server.

---

