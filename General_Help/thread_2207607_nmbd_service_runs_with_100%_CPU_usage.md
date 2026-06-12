---
title: "nmbd service runs with 100% CPU usage"
date: 2014-02-24
forum: General Help
---

### Post by sdoolman on 2014-02-24
Hello,

Today I fired up a terminal to check my Ubuntu Server 12.04 status and was surprised to see my CPU eaten up by the 'nmbd' service.
I tried restarting both Samba service , Nmbd service and even the whole system, but every time it returns and stuck at 100% CPU usage (according to 'top').
In addition, the server cannot be found by name in all my PCs, which actually makes sense...
I tried googling but found nothing regarding this issue, did anyone experience this before?

Thanks in advance!

:confused:

---

### Post by bab1 on 2014-02-24
> **sdoolman said:**
> Hello,

Today I fired up a terminal to check my Ubuntu Server 12.04 status and was surprised to see my CPU eaten up by the 'nmbd' service.
I tried restarting both Samba service , Nmbd service and even the whole system, but every time it returns and stuck at 100% CPU usage (according to 'top').
In addition, the server cannot be found by name in all my PCs, which actually makes sense...
I tried googling but found nothing regarding this issue, did anyone experience this before?

Thanks in advance!

:confused:Did you configure the NETBIOS name in your smb.conf file?  What version of Samba are you using?  What did you do to configure Samba shares?

---

### Post by sdoolman on 2014-02-24
I'm using version 3.6.3.
I do not recall configuring the NETBIOS manually, where is it located in smb.conf? Maybe I'll look for potential mistake.
I created few shares manually in the smb.conf, and they are all working fine for quite a while.
What can cause this strange behavior?

---

### Post by bab1 on 2014-02-24
> **sdoolman said:**
> I'm using version 3.6.3.
I do not recall configuring the NETBIOS manually, where is it located in smb.conf? Maybe I'll look for potential mistake.
I created few shares manually in the smb.conf, and they are all working fine for quite a while.
What can cause this strange behavior?

Post the output of this```
smbtree -d3
```

Put the output between the code blocks created by clicking on the [SIZE=4]#[/SIZE] icon at the top middle of the editor formating.

---

### Post by sdoolman on 2014-02-24
I'm getting an output like this:

```

lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface br0 ip=fe80::20e:cff:febc:97ce%br0 bcast=fe80::ffff:ffff:ffff:ffff%br0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=fe80::216:17ff:fefa:cc0%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=fe80::21b:21ff:fe0c:75f%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface br0 ip=10.0.0.4 bcast=10.0.0.255 netmask=255.255.255.0
Enter stavdoo's password:
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
Connecting to host=10.0.0.4
Connecting to 10.0.0.4 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>

```

and if I pipe the output to a file i'm getting the actual tree of shares:

```

        \\WSSERVER                      WSSERVER server (Samba, Ubuntu)
                \\WSSERVER\IPC$                 IPC Service (WSSERVER server (Samba, Ubuntu))
                \\WSSERVER\Archive              Public share
                \\WSSERVER\Musicals             Public share
                \\WSSERVER\Docu                 Public share
                \\WSSERVER\Incoming             Public share
                \\WSSERVER\Games                Public share
                \\WSSERVER\Live Shows           Public share
                \\WSSERVER\Photos               Public share
                \\WSSERVER\Music                Public share
                \\WSSERVER\Kids Series          Public share
                \\WSSERVER\Series               Public share
                \\WSSERVER\Kids Movies          Public share
                \\WSSERVER\Movies               Public share
                \\WSSERVER\print$               Printer Drivers

```

does this information help?

---

### Post by bab1 on 2014-02-24
> **sdoolman said:**
> I'm getting an output like this:

```

lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface br0 ip=fe80::20e:cff:febc:97ce%br0 bcast=fe80::ffff:ffff:ffff:ffff%br0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=fe80::216:17ff:fefa:cc0%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=fe80::21b:21ff:fe0c:75f%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface br0 ip=10.0.0.4 bcast=10.0.0.255 netmask=255.255.255.0
Enter stavdoo's password:
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
Connecting to host=10.0.0.4
Connecting to 10.0.0.4 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>

```

and if I pipe the output to a file i'm getting the actual tree of shares:

```

        \\WSSERVER                      WSSERVER server (Samba, Ubuntu)
                \\WSSERVER\IPC$                 IPC Service (WSSERVER server (Samba, Ubuntu))
                \\WSSERVER\Archive              Public share
                \\WSSERVER\Musicals             Public share
                \\WSSERVER\Docu                 Public share
                \\WSSERVER\Incoming             Public share
                \\WSSERVER\Games                Public share
                \\WSSERVER\Live Shows           Public share
                \\WSSERVER\Photos               Public share
                \\WSSERVER\Music                Public share
                \\WSSERVER\Kids Series          Public share
                \\WSSERVER\Series               Public share
                \\WSSERVER\Kids Movies          Public share
                \\WSSERVER\Movies               Public share
                \\WSSERVER\print$               Printer Drivers

```

does this information help?
It appears you are using IPv6 and a bridge.  These are not commonly used.  Is this machine part of a VM network. If I was running this setup I would not use the nmbd daemon at all.  I would configure the server's NETBIOS NAME explicitly by adding this to the [global] section of the smb.conf file```
netbios name = WSSERVER
```...This turns off the nmbd daemon.

See if that helps. 

I believe you missed some of the output after the ```

name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>

```

With all the IPv6 addressing space and a bridged network I can see how broadcasts can be a problem.  You may have to alter your network to accommodate Samba v3.  If you route the VM's you will need to use a WINS server and not use bcast as a means of locating hosts.

NETBIOS uses namespace to find IP addresses via dynamic lookup tables, unlike DNS which traditionally uses static mapping of IP addresses to hostnames,  NETBIOS and DNS are very different in this respect.

---

### Post by sdoolman on 2014-02-25
Thanks for the detailed reply, unfortunately I tried both explicitly declare the netbios name and [disable IPv6 globally by editing sysctl.conf file]("http://askubuntu.com/questions/41543/how-to-dynamically-enable-and-disable-ipv6-on-an-interface").

My machine is not a part of a VM network, though it is using a bridge connection between 3 interfaces which I've connected to numerous other machines and my router.
If I disable nmbd service manually it seems everything still works great, so why is it still starting every time I boot the machine?

---

### Post by bab1 on 2014-02-25
> **sdoolman said:**
> Thanks for the detailed reply, unfortunately I tried both explicitly declare the netbios name and [disable IPv6 globally by editing sysctl.conf file]("http://askubuntu.com/questions/41543/how-to-dynamically-enable-and-disable-ipv6-on-an-interface").

My machine is not a part of a VM network, though it is using a bridge connection between 3 interfaces which I've connected to numerous other machines and my router.

Describe the network topology (physically and IP addresses).
> 
If I disable nmbd service manually it seems everything still works great, so why is it still starting every time I boot the machine?

What's "*still starting every time I boot the machine?*"?

The problem appears to be that you have misconfigured the networking somewhere.  I would have no idea without further diagnosis.  My guess is you have created a network looping situation. 

Explain why you have 3 NIC's in a single computer for your network.

---

### Post by sdoolman on 2014-02-25
I have a home network with both Windows and Linux machines. As you can see I have a server machine called WSSERVER which provides media to all other machines.
It is actually connected to 2 other machines directly and to the router - hence the bridge.
All the machines in my network receive IP address by DHCP server located in the router, all except those 2 machines which receive an internal IP address from WSSERVER.
I can provide some ifconfig outputs if that helps, anything particular?

---

