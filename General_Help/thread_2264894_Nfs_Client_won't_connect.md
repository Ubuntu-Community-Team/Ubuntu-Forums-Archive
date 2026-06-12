---
title: "Nfs: Client won't connect"
date: 2015-02-11
forum: General Help
---

### Post by Harry_Parson on 2015-02-11
New to Ubuntu. Running 14.04 64bit. Have installed nfs-common, confirmed it's installed, rebooted and tried to mount my non-Ubuntu server unsuccessfully. All the other boxes on the LAN have no problem. Checked to see if the nfs module is loaded.

```
# modprobe nfs
modprobe: FATAL: Module nfs not found.
```

Somehow I don't think it's going to work without the module. Could someone please give me a suggestion.

---

### Post by TheFu on 2015-02-11
Does the normal Ubuntu Help not help?
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by Harry_Parson on 2015-02-12
> **TheFu said:**
> Does the normal Ubuntu Help not help?
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)


I got up to the second instruction which produced...

```
$ sudo mount -t nfs -o proto=tcp,port=2049 192.168.1.105:/ /mnt
mount.nfs: No such device
```

...which is why I wondered if the nfs module was loaded. Apparently not. Any other suggestions?

---

### Post by TheFu on 2015-02-12
Did you export anything from the other system?  I've never seen / exported before. Is that allowed?

```
$ lsmod |grep nfs
nfsv3                  34001  1 
nfsd                  247797  2 
auth_rpcgss            48979  1 nfsd
nfs_acl                12733  2 nfsd,nfsv3
nfs                   209382  2 nfsv3
lockd                  78518  3 nfs,nfsd,nfsv3
sunrpc                242738  20 nfs,nfsd,auth_rpcgss,lockd,nfsv3,nfs_acl
fscache                56756  1 nfs
```
is from an nfs client here. I mount using autofs, not a direct mount. If mount.nfs doesn't exist, that would be a problem. If you follow those instructions, it will work.
What is the other non-ubuntu box and which version of NFS is it exporting?

---

### Post by Harry_Parson on 2015-02-12
> **TheFu said:**
> Did you export anything from the other system?  I've never seen / exported before. Is that allowed?

```
$ lsmod |grep nfs
nfsv3                  34001  1 
nfsd                  247797  2 
auth_rpcgss            48979  1 nfsd
nfs_acl                12733  2 nfsd,nfsv3
nfs                   209382  2 nfsv3
lockd                  78518  3 nfs,nfsd,nfsv3
sunrpc                242738  20 nfs,nfsd,auth_rpcgss,lockd,nfsv3,nfs_acl
fscache                56756  1 nfs
```
is from an nfs client here. I mount using autofs, not a direct mount. If mount.nfs doesn't exist, that would be a problem. If you follow those instructions, it will work.
What is the other non-ubuntu box and which version of NFS is it exporting?

My error. The quote should have read...

```
$ sudo mount -t nfs -o proto=tcp,port=2049 192.168.1.105:/mnt/hd /mnt
mount.nfs: No such device
```

And yes / can be exported under my server's OS.

When I invoke...

```
$  lsmod |grep nfs
(trusty)ion@localhost:~$ 

```

...I get nothing.

Mount.nfs does exist as this indicates.

```
$ sudo mount.nfs
mount.nfs: no mount point provided 
```

The server is running openSUSE 12.2 and the version is NFSv4. The server works with several other boxes as clients.

Thanks for the help.

---

### Post by steeldriver on 2015-02-12
What does 

```

showmount -e 192.168.1.105

```

say?

---

### Post by TheFu on 2015-02-12
Please copy/paste unaltered output so we don't have to guess what is actually happening too. As you see, we headed in the (likely) wrong direction already.
Is forcing v3 an option? [http://ubuntuforums.org/showthread.php?t=2264918&highlight=nfsv4](http://ubuntuforums.org/showthread.php?t=2264918&highlight=nfsv4)

---

### Post by Harry_Parson on 2015-02-13
> **steeldriver said:**
> What does 

```

showmount -e 192.168.1.105

```

say?

showmount is not installed and when I....

```
$ sudo apt-get install showmount
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package showmount
```

---

### Post by bab1 on 2015-02-13
> **Harry_Parson said:**
> showmount is not installed and when I....

```
$ sudo apt-get install showmount
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package showmount
```

The package is ***nfs-common***.

---

### Post by Harry_Parson on 2015-02-13
> **TheFu said:**
> Please copy/paste unaltered output so we don't have to guess what is actually happening too. As you see, we headed in the (likely) wrong direction already.
Is forcing v3 an option? [http://ubuntuforums.org/showthread.php?t=2264918&highlight=nfsv4](http://ubuntuforums.org/showthread.php?t=2264918&highlight=nfsv4)

Following your advice of using the above link, I invoked.....

```
$ sudo mount -vvv -t nfs -o vers=3 192.168.1.105:/mnt/hd /mnt
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: spec:  "192.168.1.105:/mnt/hd"
mount: node:  "/mnt"
mount: types: "nfs"
mount: opts:  "vers=3"
mount: external mount: argv[0] = "/sbin/mount.nfs"
mount: external mount: argv[1] = "192.168.1.105:/mnt/hd"
mount: external mount: argv[2] = "/mnt"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,vers=3"
mount.nfs: timeout set for Fri Feb 13 08:17:49 2015
mount.nfs: rpc.statd is not running but is required for remote locking.
mount.nfs: Either use '-o nolock' to keep locks local, or start statd.
mount.nfs: an incorrect mount option was specified
```

...and again with nolock added...

```
$ sudo mount -vvv -t nfs -o nolock,vers=3 192.168.1.105:/mnt/hd /mnt
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: spec:  "192.168.1.105:/mnt/hd"
mount: node:  "/mnt"
mount: types: "nfs"
mount: opts:  "nolock,vers=3"
mount: external mount: argv[0] = "/sbin/mount.nfs"
mount: external mount: argv[1] = "192.168.1.105:/mnt/hd"
mount: external mount: argv[2] = "/mnt"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,nolock,vers=3"
mount.nfs: timeout set for Fri Feb 13 08:19:46 2015
mount.nfs: trying text-based options 'nolock,vers=3,addr=192.168.1.105'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 192.168.1.105 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=17
mount.nfs: trying 192.168.1.105 prog 100005 vers 3 prot UDP port 45235
mount.nfs: mount(2): No such device
mount.nfs: No such device

```

There's that "mount.nfs: No such device" again!

---

### Post by Harry_Parson on 2015-02-13
> **bab1 said:**
> The package is ***nfs-common***.

Yes but it is installed.

```
$ sudo apt-get install nfs-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nfs-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
```

---

### Post by steeldriver on 2015-02-13
Is your PATH messed up? does

```

/sbin/showmount -e 192.168.1.105

```

work? 

AFAIK it should be provided by nfs-common - see [http://packages.ubuntu.com/trusty/amd64/nfs-common/filelist](http://packages.ubuntu.com/trusty/amd64/nfs-common/filelist) but you could check with

```

dpkg -L nfs-common

```

---

### Post by Harry_Parson on 2015-02-13
> **steeldriver said:**
> Is your PATH messed up? does

```

/sbin/showmount -e 192.168.1.105

```

work? 

AFAIK it should be provided by nfs-common - see [http://packages.ubuntu.com/trusty/amd64/nfs-common/filelist](http://packages.ubuntu.com/trusty/amd64/nfs-common/filelist) but you could check with

```

dpkg -L nfs-common

```

The problem was I was invoking showmount as user not sudo.

[CODE$ sudo showmount -e 192.168.1.105
Export list for 192.168.1.105:
/mnt/hd 192.168.1.200,192.168.1.101,192.168.1.100][/CODE]

And here's my ifconfig to confirm my client address.

```
[$ sudo ifconfig                  
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9048 (9.0 KB)  TX bytes:9048 (9.0 KB)

wlan0     Link encap:Ethernet  HWaddr 38:b1:db:76:b1:4f  
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3ab1:dbff:fe76:b14f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8011 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7345 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4995428 (4.9 MB)  TX bytes:1379370 (1.3 MB)/CODE]

And here is a ping to confirm again.

[CODE]$ sudo ping 192.168.1.105
PING 192.168.1.105 (192.168.1.105) 56(84) bytes of data.
64 bytes from 192.168.1.105: icmp_seq=1 ttl=64 time=3.67 ms
64 bytes from 192.168.1.105: icmp_seq=2 ttl=64 time=2.39 ms
^C
--- 192.168.1.105 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.399/3.038/3.678/0.641 ms
```

Thanks for the assistance.

---

### Post by TheFu on 2015-02-13
Wifi and NFS - scary.  I'd do a read-only mount with soft and a shortened timeout in the options.
OTOH, lots of other people use NFS over wifi, I just don't.

BTW, I've done over 1200 wifi deployments around the world. I don't use wifi at home unless there isn't any other choice.  Even my chromebook, which is wifi only, has a USB-2-GigE wired connection.  Wifi isn't as stable as people think it is.  The bandwidth fluctuates wildly - humans using email and surfing don't notice, but computers do.

Even if you can't do this long term except over wifi, can you troubleshoot with a wired connection?

---

### Post by steeldriver on 2015-02-13
So let's go back to why your lsmod appeared to show no nfs-related kernel modules. I can only think of a few reasons for that:

[LIST=1]
[*]the module(s) are blacklisted
[*]the client needs a reboot in order to load the modules
[*]something went wrong with the nfs-common or current kernel install
[*]the kernel is configured with nfs built-in rather than as a module
[/LIST]

Did you try

```

sudo modprobe -v nfs

```

yet? does it report anything interesting?

---

### Post by Harry_Parson on 2015-02-13
> **TheFu said:**
> Wifi and NFS - scary.  I'd do a read-only mount with soft and a shortened timeout in the options.
OTOH, lots of other people use NFS over wifi, I just don't.

BTW, I've done over 1200 wifi deployments around the world. I don't use wifi at home unless there isn't any other choice.  Even my chromebook, which is wifi only, has a USB-2-GigE wired connection.  Wifi isn't as stable as people think it is.  The bandwidth fluctuates wildly - humans using email and surfing don't notice, but computers do.

Even if you can't do this long term except over wifi, can you troubleshoot with a wired connection?

Many thanks for your honest answer. I also try to not use wireless, but like you I have a Chromebook with no wire connector. However I will try once I get a USB wired connector. Tricky in a small town in Mexico. On the other hand would you suggest I try using another file system with wireless?

---

### Post by Harry_Parson on 2015-02-13
> **steeldriver said:**
> So let's go back to why your lsmod appeared to show no nfs-related kernel modules. I can only think of a few reasons for that:

[LIST=1]
[*]the module(s) are blacklisted 
[*]the client needs a reboot in order to load the modules 
[*]something went wrong with the nfs-common or current kernel install 
[*]the kernel is configured with nfs built-in rather than as a module 
[/LIST]

Did you try

```

sudo modprobe -v nfs

```

yet? does it report anything interesting?

I suspect answer number 3. So a new install is running at this moment and I will check your modprobe option when it is done.

Thank you.

---

### Post by TheFu on 2015-02-13
```
sudo modprobe -v nfs
```
doesn't return anything for my working NFS client.
lsmod does - see above.

---

### Post by steeldriver on 2015-02-13
@TheFu I would expect that behavior if the module is already loaded

---

### Post by Harry_Parson on 2015-02-13
> **steeldriver said:**
> 
Did you try

```

sudo modprobe -v nfs

```

yet? does it report anything interesting?

```
$ sudo modprobe -v nfs
modprobe: FATAL: Module nfs not found.

$ lsmod | grep nfs
(trusty)ion@localhost:~$ 


```
No nothing interesting.

---

### Post by bab1 on 2015-02-13
> **Harry_Parson said:**
> 
```
$ sudo modprobe -v nfs
modprobe: FATAL: Module nfs not found.

```
If it has not been pointed out earlier; This command adds a module (driver).  Since you did not provide a module the command returns the FATAL error. 

```

$ lsmod | grep nfs
(trusty)ion@localhost:~$ 


```
No nothing interesting.
This IS interesting.  You should have modules (drivers) for *nfs*.  Without the modules you don't have, at the very least, mount.nfs (mount -t nfs).  These are all part of the package ***nfs-common***.  Look at the package description either on the web (google nfs-common package) or using dpkg ( [COLOR="#0000FF"] You can use: dpkg -s nfs-common[/COLOR]).

See if you can do this```
man mount.nfs
```

What do you get if you use this comand```
pgrep -l lockd
```...(hint) if you don't get anything then I would say that  *nfs-common* is NOT installed

---

### Post by steeldriver on 2015-02-13
The actual kernel module(s) should be provided by the kernel package, rather than the nfs-common package, I think e.g.

```

$ find /lib/modules/`uname -r` -name 'nfs.ko'
/lib/modules/3.2.0-75-generic-pae/kernel/fs/nfs/nfs.ko

$ dpkg -S /lib/modules/3.2.0-75-generic-pae/kernel/fs/nfs/nfs.ko
linux-image-3.2.0-75-generic-pae: /lib/modules/3.2.0-75-generic-pae/kernel/fs/nfs/nfs.ko

```

@Harry_Parson, can we also see

```

grep '_NFS' /boot/config-`uname -r`

```
please?

---

### Post by Harry_Parson on 2015-02-13
> **bab1 said:**
> This IS interesting.  You should have modules (drivers) for *nfs*.  Without the modules you don't have, at the very least, mount.nfs (mount -t nfs).  These are all part of the package ***nfs-common***.  Look at the package description either on the web (google nfs-common package) or using dpkg ( [COLOR=#0000FF] You can use: dpkg -s nfs-common[/COLOR]).

See if you can do this```
man mount.nfs
```

What do you get if you use this comand```
pgrep -l lockd
```...(hint) if you don't get anything then I would say that  *nfs-common* is NOT installed

```
$ sudo man mount.nfs
No manual entry for mount.nfs
```

```
$ sudo pgrep -l lockd
21 kblockd
```

But as I have already posted...

```
$ sudo apt-get install nfs-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nfs-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Harry_Parson on 2015-02-13
> **steeldriver said:**
> The actual kernel module(s) should be provided by the kernel package, rather than the nfs-common package, I think e.g.

```

$ find /lib/modules/`uname -r` -name 'nfs.ko'
/lib/modules/3.2.0-75-generic-pae/kernel/fs/nfs/nfs.ko

$ dpkg -S /lib/modules/3.2.0-75-generic-pae/kernel/fs/nfs/nfs.ko
linux-image-3.2.0-75-generic-pae: /lib/modules/3.2.0-75-generic-pae/kernel/fs/nfs/nfs.ko

```

@Harry_Parson, can we also see

```

grep '_NFS' /boot/config-`uname -r`

```
please?

```
$ find /lib/modules/`uname -r` -name 'nfs.ko'
(trusty)ion@localhost:~$
```

```
$ sudo dpkg -S /lib/modules/3.2.0-75-generic-pae/kernel/fs/nfs/nfs.ko
dpkg-query: no path found matching pattern /lib/modules/3.2.0-75-generic-pae/kernel/fs/nfs/nfs.ko
```

```
$ sudo grep '_NFS' /boot/config-`uname -r`
grep: /boot/config-3.8.11: No such file or directory
```

Wait a minure. Does kernel 3.8.11 sound right to you?

```
$ uname -ra
Linux localhost 3.8.11 #1 SMP Thu Feb 5 20:32:47 PST 2015 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by bab1 on 2015-02-13
> **Harry_Parson said:**
> ```
$ sudo man mount.nfs
No manual entry for mount.nfs
```

```
$ sudo pgrep -l lockd
21 kblockd
```

But as I have already posted...

```
$ sudo apt-get install nfs-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nfs-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
That doesn't mean too much to me.  Part of the nfs-common package is the man pages for mount.nfs ```
/usr/share/man/man8/mount.nfs.8.gz
```
It appears you do not have that.  Of course there can be something else wrong.  Some of the package is installed however or you wouldn't have lockd (kblockd).

[COLOR="#0000FF"]Edit:  Here is a list of all that is in the nfs-common package:[/COLOR]   [http://packages.ubuntu.com/trusty/amd64/nfs-common/filelist\]("http://packages.ubuntu.com/trusty/amd64/nfs-common/filelist\")

---

### Post by bab1 on 2015-02-13
> **Harry_Parson said:**
> ```
$ find /lib/modules/`uname -r` -name 'nfs.ko'
(trusty)ion@localhost:~$
```

```
$ sudo dpkg -S /lib/modules/3.2.0-75-generic-pae/kernel/fs/nfs/nfs.ko
dpkg-query: no path found matching pattern /lib/modules/3.2.0-75-generic-pae/kernel/fs/nfs/nfs.ko
```

```
$ sudo grep '_NFS' /boot/config-`uname -r`
grep: /boot/config-3.8.11: No such file or directory
```

Wait a minure. Does kernel 3.8.11 sound right to you?

```
$ uname -ra
Linux localhost 3.8.11 #1 SMP Thu Feb 5 20:32:47 PST 2015 x86_64 x86_64 x86_64 GNU/Linux
```
You should substitute your kernel for the one @steeldriver supplied.  But it really should not matter.  The kernel should come with all of that. It's not something you need to configure normally.

BUT......... If you are using a NON default kernel 3.8 then anything is possible.

---

### Post by steeldriver on 2015-02-13
What kind of machine is this? that doesn't seem to be an Ubuntu uname output or any kernel that appears to have shipped (according to packages.ubuntu.com). Is it a chromebook maybe?

---

### Post by bab1 on 2015-02-13
> **steeldriver said:**
> What kind of machine is this? that doesn't seem to be an Ubuntu uname output or any kernel that appears to have shipped (according to packages.ubuntu.com). Is it a chromebook maybe?

+1000

This is the kernel on a 1 week old install of 64 bit: *3.13.0-45-generic*

---

### Post by Harry_Parson on 2015-02-13
> **steeldriver said:**
> What kind of machine is this? that doesn't seem to be an Ubuntu uname output or any kernel that appears to have shipped (according to packages.ubuntu.com). Is it a chromebook maybe?

Yes it is an Acer C720-2848 Chromebook. I did post in an earlier response....

[HTML] I also try to not use wireless, but like you I have a Chromebook with no wire connector.[/HTML]

---

### Post by Harry_Parson on 2015-02-13
Thanks to all of you for the time you put in trying to solve my problem. But I think I'm flogging a dead horse. Ubuntu 14.04 with a 3.8.11 kernel was reported to be an easy solution for working with my Chromebook. And in truth the installation was very easy and everything worked, except the one thing I need to tie into my LAN. I have spent too much of your time and mine too. I will have to look at another distribution for a "simple" solution.

Thanks again.

---

### Post by bab1 on 2015-02-14
> **Harry_Parson said:**
> Thanks to all of you for the time you put in trying to solve my problem. But I think I'm flogging a dead horse. Ubuntu 14.04 with a 3.8.11 kernel was reported to be an easy solution for working with my Chromebook. And in truth the installation was very easy and everything worked, except the one thing I need to tie into my LAN. I have spent too much of your time and mine too. I will have to look at another distribution for a "simple" solution.

Thanks again.
I don't think it's the distro.  I think it's the type of install.  What I mean by that is you probably installed Ubuntu while leaving the Chrome OS kernel.  My sense is that Chrome OS has no provision for NFS in the kernel.

You can do as you please, but be aware of HOW + what you are installing.

---

### Post by TheFu on 2015-02-14
Here's a Chromebook kernel:
```
$ uname -ra
Linux c720 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:37:48 UTC 2015 i686 i686 i686 GNU/Linux
```
But it has Ubuntu Server x32 installed, not ChromeOS.

NFS works, BTW.

---

### Post by TheFu on 2015-02-14
> **Harry_Parson said:**
> Thanks to all of you for the time you put in trying to solve my problem. But I think I'm flogging a dead horse. Ubuntu 14.04 with a 3.8.11 kernel was reported to be an easy solution for working with my Chromebook. And in truth the installation was very easy and everything worked, except the one thing I need to tie into my LAN. I have spent too much of your time and mine too. I will have to look at another distribution for a "simple" solution.

Thanks again.

Another distro using the same kernel won't help.

Just install a full Ubuntu on your C720, with the stock kernel. If you use 14.10, then you won't have to rebuild the touchpad drivers with every new kernel.  I refuse to run a non-LTS release, so I'll be rebuilding the kernel drivers for the touchpad every few weeks.  If you can't do that task without a mouse, you'll want to plan on 14.10, 15.04, 15.10, 16.04 updates over the next 16 months.

This explains the touchpad fix: [http://blog.jdpfu.com/2014/04/18/easy-acer-c720-ubuntu-14-04](http://blog.jdpfu.com/2014/04/18/easy-acer-c720-ubuntu-14-04)
Here's the install how-to: [https://blogs.fsfe.org/the_unconventional/2014/04/20/c720-debian/](https://blogs.fsfe.org/the_unconventional/2014/04/20/c720-debian/) - shows how to get into developer mode.  I replaced the 16G m2.SSD for a 128G m2.SSD, but 64G would have been more than enough. See:
```
$ df
Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/lubuntu--vg-root  116G   27G   83G  25% /
```
32G could be enough - especially with NFS storage.  I use autofs to mount it only when requested.  That way it doesn't lock up the system when I'm not at home.
The USB3-2-ethernet adapter uses the ax88179_178a drivers. This was added in 14.04 and works well. **Unitek 3 Ports USB 3.0 Bus-Powered Hub with RJ45 10/100/1000 Gigabit Ethernet** for $24 on amazon.

That should get you started.

---

