---
title: "Can't get machines to mount nfs from fstab"
date: 2006-12-19
forum: General Help
---

### Post by StickyStyle on 2006-12-19
I am seriously going nuts with this and was hoping someone could point out my (most likely) obvious mistake ](*,)

I have a NFS share running on OS X server (10.4.6) that i would like all my desktops to mount so that i can host the mandatory gconf settings from one place (that part really isn't relevant).  From the dapper machines i can see the mount on the OS X box -
rparrish@devdesktop:/var/lib/nfs$ showmount -e 10.2.5.3
Export list for ds1:
/share/gconf (everyone)

and i can mount the share just fine with mount -
rparrish@devdesktop:~$mount -t nfs 10.2.5.3:/share/gconf/ /etc/gconf/network

however if i put that mount in my fstab it never mounts, and it doesnt report any errors in daemon.log, syslog, or messages excpept the following...
Dec 19 14:37:20 localhost rpc.statd[4578]: statd running as root. chown /var/lib/nfs/sm to choose different user

This is what the fstab line looks like -
10.2.5.3:/share/gconf /etc/gconf/network/ nfs rw 0 0

pretty basic and i have tried all kinds of different options like ro, proto=tcp, rsize, wsize, and other i cant remember.

Any tips? Please :-k

---

### Post by jdusablon on 2007-01-03
NFS entries in fstab must be DNS hostnames, not IP addresses. I ran into the same thing.

Just replace the IP address with the hostname.

---

### Post by MountainX on 2008-03-30
Can anyone elablorate on the requirement for mounting NFS shares in fstab?

I edited /etc/hosts and added a line for the ip address and hostname of my server like this:
```
192.168.100.100 MyServer
```

Then in /etc/fstab I used this:
```
//MyServer:/Documents /home/myuser/Documents nfs rw,hard,intr 0 0
```

The results is this error:
```
$ sudo mount -a -t nfs
[COLOR="Red"]**mount.nfs: can't get address for //MyServer**[/COLOR]

```

```

$ ping MyServer
PING MyServer.hsd1.my.isp.org. (192.168.100.100) 56(84) bytes of data.
64 bytes from MyServer.hsd1.my.isp.org. (192.168.100.100): icmp_seq=1 ttl=128 time=0.081 ms
64 bytes from MyServer.hsd1.my.isp.org. (192.168.100.100): icmp_seq=2 ttl=128 time=0.080 ms
64 bytes from MyServer.hsd1.my.isp.org. (192.168.100.100): icmp_seq=3 ttl=128 time=0.079 ms
64 bytes from MyServer.hsd1.my.isp.org. (192.168.100.100): icmp_seq=4 ttl=128 time=0.114 ms

--- MyServer.hsd1.my.isp.org. ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.079/0.088/0.114/0.017 ms

```

What am I missing?

BTW, I forgot to mention, mounting manually works fine:

```

$ sudo mount -t nfs -vvv 192.168.100.100:Documents /home/myuser/Documents
mount: fstab path: "/etc/fstab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: spec:  "192.168.100.100:Documents"
mount: node:  "/home/myuser/Documents"
mount: types: "nfs"
mount: opts:  "(null)"
mount: external mount: argv[0] = "/sbin/mount.nfs"
mount: external mount: argv[1] = "192.168.100.100:Documents"
mount: external mount: argv[2] = "/home/myuser/Documents"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw"
mount.nfs: trying 192.168.100.100 prog 100003 vers 3 prot TCP port 2049
mount.nfs: trying 192.168.100.100 prog 100005 vers 3 prot UDP port 1048
192.168.100.100:Documents on /home/myuser/Documents type nfs (rw)
/$ 

```

UPDATE:
```
$ nslookup
** server can't find MyServer: NXDOMAIN
```
What does that last line mean?

---

### Post by MountainX on 2008-03-30
As I'm googling this, I found
[http://www.lbl.gov/ITSD/CIS/faqs/UNIX_Faq/28.html](http://www.lbl.gov/ITSD/CIS/faqs/UNIX_Faq/28.html)

The error looks the same as the one I just posted above, but I sure don't think this sounds like the solution. I mean, is setting up NFS really this complicated? :confused:

Why is my Linux box unable to mount NFS, and always seem slow to connect
The following question was posted to the Linux Users Group
I was wondering if this issue has been raised before. I have a problem and I have seen other experiencing as well. Whenever I am using a machine with a DCHP assigned IP address, I lose access to certain services. Specifically, I cannot NFS mount. I believe this is a default option in most modern NFS servers, they will fail to authenticate requests from IP addresses which they cannot do a reverse name lookup on. For example, when I request a DHCP address for my laptop, I am assigned 128.3.11.225. But there is no PTR record for this address.
# nslookup -sil 128.3.11.225
Server: 128.3.34.186
Address: 128.3.34.186#53
** server can't find 225.11.3.128.in-addr.arpa.: NXDOMAIN

Response to the question
I was able to work around some of these issues by using Samba's features of WINS registration of my local hostname as a netbios name. This is actually very easy to do. Edit the smb.conf file and activate WINS by uncommenting the line 'wins server = ' line and adding the WINS server's IP (128.3.132.9). Just start Samba, and your set.
Your new reversely mapped hostname is [HOSTNAME].wins.lbl.gov.
Contributed by Greg kurtzer

---

### Post by AndyCooll on 2008-03-30
Setting up NFS in fstab *shouldn't* be difficult. I can say this now, for these days it takes me seconds ...however I can remember finding it painful at the beginning.

In spite of what has been said it CAN be IP address based, provided the server with the shares has fixed IP address of course,

My line in fstab at its most basic usually takes the following format:
```
192.168.1.2:/share /mnt/share nfs defaults 0 0
```
Where 192.168.1.2:/share is the shared folder on my server
/mnt/share is the mount point I've created
nfs defaults 0 0 are the basic mount instructions.

Obviously you can take further advanced steps, such as changing from "defaults", or using the DNS settings if you don't wish to use a fixed IP address.

:cool:

---

### Post by MountainX on 2008-03-30
Thanks for the info. It is good to know I can use an IP address for NFS mounts in fstab. (Another post said that couldn't be done.)

So what could my problem be? 

Wow - solved it. Here was the problem:
When I mount shares in fstab with cifs or samba, I always start like this:
//192.168.x.x
That doesn't work with nfs. All I had to do was remove the two leading slashes! Now it works! 

Seriously, this took me about 8 hours to figure out! That's four hours per character! lol

---

### Post by MountainX on 2008-03-31
Here are two other tips I found useful:

1. Use "**hard,intr**" options. "Hard mounts with the interruptible option enabled is the recommended method of mounting remote filesystems." See [http://docsrv.sco.com:507/en/NetAdminG/nfsD.nfsmount.html](http://docsrv.sco.com:507/en/NetAdminG/nfsD.nfsmount.html)

2. From [http://unixfoo.blogspot.com/2008/02/nfs-mount-options.html](http://unixfoo.blogspot.com/2008/02/nfs-mount-options.html)

Some important nfs mount options in Linux.

    * tcp - Specifies for the NFS mount to use the TCP protocol instead of UDP.
    * rsize=8192 and wsize=8192 - These settings speed up NFS communication for reads (rsize) and writes (wsize) by setting a larger data block size, in bytes, to be transferred at one time. Do performance tests before changing these values.
    * hard or soft - Specifies whether the program using a file via an NFS connection should stop and wait (hard) for the server to come back online if the host serving the exported file system is unavailable, or if it should report an error (soft). If hard is specified, the user cannot terminate the process waiting for the NFS communication to resume unless the intrsoft, is specified, the user can set an additional timeo=<value> option, where <value> specifies the number of seconds to pass before the error is reported. option is also specified.
    * nolock - Disables file locking. This setting is occasionally required when connecting to older NFS servers.
    * noexec - Prevents execution of binaries on mounted file systems. This is useful if the system is mounting a non-Linux file system via NFS containing incompatible binaries.
    * intr - Allows NFS requests to be interrupted if the server goes down or cannot be reached.
    * nfsvers=2 or nfsvers=3 - Specifies which version of the NFS protocol to use.
    *
      nosuid - Disables set-user-identifier or set-group-identifier bits. This prevents remote users from gaining higher privileges by running a setuid program.

---

### Post by MountainX on 2008-04-01
> **jdusablon said:**
> NFS entries in fstab must be DNS hostnames, not IP addresses. I ran into the same thing.

Just replace the IP address with the hostname.

I want to let everyone know that NFS entries in fstab can be IP addresses. (Just don't start either of them with "//")

---

