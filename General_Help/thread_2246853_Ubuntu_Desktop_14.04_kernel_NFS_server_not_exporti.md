---
title: "Ubuntu Desktop 14.04 kernel NFS server not exporting static device nodes"
date: 2014-10-03
forum: General Help
---

### Post by daniel-glasser on 2014-10-03
I have a problem with NFS serving "/dev" out of an exported file system that just started happening this week.  I don't know when, but some time between Monday and after I applied updates today, and nothing I've tried has made any difference.

I export the development root file system for a PowerPC based embedded platform from my Ubuntu workstation (the one in NOR flash on the device is minimal).  

[LIST]
[*]The exported fs tree was created using buildroot, and has been unpacked as "/usr/local/exported/buildroot-nfs".
[*]The client root file system has a static "/dev".
[*]The host's "/etc/fstab" includes the following line:
[/LIST]
[INDENT=2][FONT=lucida console]/usr/local/exported/buildroot-nfs /buildroot-nfs none bind 0 0[/FONT][/INDENT]

[LIST]
[*]The exports line is:
[/LIST]
[INDENT=2][FONT=lucida console]/buildroot-nfs	172.16.96.0/24(rw,fsid=0,insecure,no_subtree_check,async,no_root_squash)[/FONT][/INDENT]

[LIST=|INDENT=1]
[*]Bootp is used by the client to get its network parameters and such (I'm using isc-dhcp-server).  Here is how I have this configured:
       [FONT=lucida console]subnet 172.16.96.0 netmask 255.255.254.0 {
        range 172.16.96.200 172.16.96.220;
        option routers 172.16.96.1;
        option broadcast-address 172.16.96.255;
        default-lease-time 600;
        max-lease-time 7200;
    }
    host RP1011 {
        hardware ethernet FC:FB:FA:00:00:01;
        server-name "172.16.96.1";
        filename "uImage";
        fixed-address 172.16.96.4;
        option root-path "/buildroot-nfs";
    }
[FONT=arial](The device tree used for this is in NOR flash on the client)[/FONT]
[/FONT]
[*]On the host system, the exported file system's "/dev" directory structure is intact and has all of the required device nodes defined correctly for the client kernel's build:
[FONT=lucida console]$ ls -ld /buildroot-nfs/dev
drwxr-xr-x 6 root root 4096 Nov 21  2013 /buildroot-nfs/dev
$ ls -l /buildroot-nfs/dev
[/FONT][FONT=lucida console]total 16[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  5,   1 Nov 21  2013 console[/FONT]
[FONT=lucida console]drwxr-xr-x 2 root root    4096 Nov 21  2013 input[/FONT]
[FONT=lucida console]crw-r----- 1 root root  1,   2 Nov 21  2013 kmem[/FONT]
[FONT=lucida console]lrwxrwxrwx 1 root root      10 Aug  9 09:10 log -> ../tmp/log[/FONT]
[FONT=lucida console]brw-r----- 1 root root  7,   0 Nov 21  2013 loop0[/FONT]
[FONT=lucida console]brw-r----- 1 root root  7,   1 Nov 21  2013 loop1[/FONT]
[FONT=lucida console]crw-r----- 1 root root  1,   1 Nov 21  2013 mem[/FONT]
[FONT=lucida console]crw-r----- 1 root root 90,   0 Nov 21  2013 mtd0[/FONT]
[FONT=lucida console]crw-r----- 1 root root 90,   2 Nov 21  2013 mtd1[/FONT]
[FONT=lucida console]crw-r----- 1 root root 90,  20 Nov 21  2013 mtd10[/FONT]
[FONT=lucida console]crw-r----- 1 root root 90,  22 Nov 21  2013 mtd11[/FONT]
[FONT=lucida console]crw-r----- 1 root root 90,   4 Nov 21  2013 mtd2[/FONT]
[FONT=lucida console]crw-r----- 1 root root 90,   6 Nov 21  2013 mtd3[/FONT]
[FONT=lucida console]crw-r----- 1 root root 90,   8 Nov 21  2013 mtd4[/FONT]
[FONT=lucida console]crw-r----- 1 root root 90,  10 Nov 21  2013 mtd5[/FONT]
[FONT=lucida console]crw-r----- 1 root root 90,  12 Nov 21  2013 mtd6[/FONT]
[FONT=lucida console]crw-r----- 1 root root 90,  14 Nov 21  2013 mtd7[/FONT]
[FONT=lucida console]crw-r----- 1 root root 90,  16 Nov 21  2013 mtd8[/FONT]
[FONT=lucida console]crw-r----- 1 root root 90,  18 Nov 21  2013 mtd9[/FONT]
[FONT=lucida console]brw-r----- 1 root root 31,   0 Nov 21  2013 mtdblock0[/FONT]
[FONT=lucida console]brw-r----- 1 root root 31,   1 Nov 21  2013 mtdblock1[/FONT]
[FONT=lucida console]brw-r----- 1 root root 31,  10 Nov 21  2013 mtdblock10[/FONT]
[FONT=lucida console]brw-r----- 1 root root 31,  11 Nov 21  2013 mtdblock11[/FONT]
[FONT=lucida console]brw-r----- 1 root root 31,   2 Nov 21  2013 mtdblock2[/FONT]
[FONT=lucida console]brw-r----- 1 root root 31,   3 Nov 21  2013 mtdblock3[/FONT]
[FONT=lucida console]brw-r----- 1 root root 31,   4 Nov 21  2013 mtdblock4[/FONT]
[FONT=lucida console]brw-r----- 1 root root 31,   5 Nov 21  2013 mtdblock5[/FONT]
[FONT=lucida console]brw-r----- 1 root root 31,   6 Nov 21  2013 mtdblock6[/FONT]
[FONT=lucida console]brw-r----- 1 root root 31,   7 Nov 21  2013 mtdblock7[/FONT]
[FONT=lucida console]brw-r----- 1 root root 31,   8 Nov 21  2013 mtdblock8[/FONT]
[FONT=lucida console]brw-r----- 1 root root 31,   9 Nov 21  2013 mtdblock9[/FONT]
[FONT=lucida console]cr--r----- 1 root root 90,   1 Nov 21  2013 mtdRO0[/FONT]
[FONT=lucida console]cr--r----- 1 root root 90,   3 Nov 21  2013 mtdRO1[/FONT]
[FONT=lucida console]cr--r----- 1 root root 90,  21 Nov 21  2013 mtdRO10[/FONT]
[FONT=lucida console]cr--r----- 1 root root 90,  23 Nov 21  2013 mtdRO11[/FONT]
[FONT=lucida console]cr--r----- 1 root root 90,   5 Nov 21  2013 mtdRO2[/FONT]
[FONT=lucida console]cr--r----- 1 root root 90,   7 Nov 21  2013 mtdRO3[/FONT]
[FONT=lucida console]cr--r----- 1 root root 90,   9 Nov 21  2013 mtdRO4[/FONT]
[FONT=lucida console]cr--r----- 1 root root 90,  11 Nov 21  2013 mtdRO5[/FONT]
[FONT=lucida console]cr--r----- 1 root root 90,  13 Nov 21  2013 mtdRO6[/FONT]
[FONT=lucida console]cr--r----- 1 root root 90,  15 Nov 21  2013 mtdRO7[/FONT]
[FONT=lucida console]cr--r----- 1 root root 90,  17 Nov 21  2013 mtdRO8[/FONT]
[FONT=lucida console]cr--r----- 1 root root 90,  19 Nov 21  2013 mtdRO9[/FONT]
[FONT=lucida console]drwxr-xr-x 2 root root    4096 Nov 21  2013 net[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  1,   3 Nov 21  2013 null[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root 10,   1 Nov 21  2013 psaux[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  5,   2 Nov 21  2013 ptmx[/FONT]
[FONT=lucida console]drwxrwxr-x 2 root root    4096 Nov 21  2013 pts[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  2,   0 Nov 21  2013 ptyp0[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  2,   1 Nov 21  2013 ptyp1[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  2,   2 Nov 21  2013 ptyp2[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  2,   3 Nov 21  2013 ptyp3[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  2,   4 Nov 21  2013 ptyp4[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  2,   5 Nov 21  2013 ptyp5[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  2,   6 Nov 21  2013 ptyp6[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  2,   7 Nov 21  2013 ptyp7[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  2,   8 Nov 21  2013 ptyp8[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  2,   9 Nov 21  2013 ptyp9[/FONT]
[FONT=lucida console]brw-r----- 1 root root  1,   1 Nov 21  2013 ram[/FONT]
[FONT=lucida console]brw-r----- 1 root root  1,   0 Nov 21  2013 ram0[/FONT]
[FONT=lucida console]brw-r----- 1 root root  1,   1 Nov 21  2013 ram1[/FONT]
[FONT=lucida console]brw-r----- 1 root root  1,   2 Nov 21  2013 ram2[/FONT]
[FONT=lucida console]brw-r----- 1 root root  1,   3 Nov 21  2013 ram3[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  1,   8 Nov 21  2013 random[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root 10,  60 Nov 21  2013 rp_datad[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root 10,  62 Nov 21  2013 rp_exec[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root 10,  61 Nov 21  2013 rp_gpio[/FONT]
[FONT=lucida console]crw-r----- 1 root root 10, 135 Nov 21  2013 rtc[/FONT]
[FONT=lucida console]drwxr-xr-x 2 root root    4096 Nov 21  2013 shm[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  5,   0 Nov 21  2013 tty[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  4,   0 Nov 21  2013 tty0[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  4,   1 Nov 21  2013 tty1[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  3,   0 Nov 21  2013 ttyp0[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root 57,   0 Nov 21  2013 ttyP0[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  3,   1 Nov 21  2013 ttyp1[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root 57,   1 Nov 21  2013 ttyP1[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  3,   2 Nov 21  2013 ttyp2[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root 57,   2 Nov 21  2013 ttyP2[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  3,   3 Nov 21  2013 ttyp3[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root 57,   3 Nov 21  2013 ttyP3[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  3,   4 Nov 21  2013 ttyp4[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  3,   5 Nov 21  2013 ttyp5[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  3,   6 Nov 21  2013 ttyp6[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  3,   7 Nov 21  2013 ttyp7[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  3,   8 Nov 21  2013 ttyp8[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  3,   9 Nov 21  2013 ttyp9[/FONT]
[FONT=lucida console]crw------- 1 root root  4,  64 Nov 21  2013 ttyS0[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  4,  65 Nov 21  2013 ttyS1[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  1,   9 Nov 21  2013 urandom[/FONT]
[FONT=lucida console]crw-rw-rw- 1 root root  1,   5 Nov 21  2013 zero[/FONT]


[/LIST]
Since last November, I've been using this arrangement, first on a 13.04 system, then on a newer 14.04 system.  The client's console output looked like this (lots of verbosity preceeding this has been deleted):
[INDENT][FONT=lucida console]TCP cubic registered[/FONT][/INDENT]
[INDENT][FONT=lucida console]NET: Registered protocol family 17[/FONT][/INDENT]
[INDENT][FONT=lucida console]Registering the dns_resolver key type[/FONT][/INDENT]
[INDENT][FONT=lucida console]IP-Config: Complete:[/FONT][/INDENT]
[INDENT][FONT=lucida console]     device=eth0, addr=172.16.96.4, mask=255.255.254.0, gw=172.16.96.1,[/FONT][/INDENT]
[INDENT][FONT=lucida console]     host=gs1011, domain=, nis-domain=(none),[/FONT][/INDENT]
[INDENT][FONT=lucida console]     bootserver=172.16.96.1, rootserver=172.16.96.1, rootpath=[/FONT][/INDENT]
[INDENT][FONT=lucida console]VFS: Mounted root (nfs filesystem) on device 0:12.[/FONT][/INDENT]
[INDENT][FONT=lucida console]Freeing unused kernel memory: 144k init[/FONT][/INDENT]
[INDENT][FONT=lucida console]Starting logging: OK[/FONT][/INDENT]
[INDENT][FONT=lucida console]Initializing random number generator... done.[/FONT][/INDENT]
[INDENT][FONT=lucida console]Starting network...[/FONT][/INDENT]
[INDENT][FONT=lucida console]ip: RTNETLINK answers: File exists[/FONT][/INDENT]
[INDENT][FONT=lucida console]Starting system time setup...[/FONT][/INDENT]
[INDENT][FONT=lucida console]Before setting date, system time is Wed Dec 31 17:00:12 MST 1969[/FONT][/INDENT]
[INDENT][FONT=lucida console]After setting date, system time is Tue Sep 23 13:15:48 MDT 2014[/FONT][/INDENT]
[INDENT][FONT=lucida console]
[/FONT][/INDENT]
[INDENT][FONT=lucida console]Welcome to Buildroot[/FONT][/INDENT]
[INDENT][FONT=lucida console]buildroot login:[/FONT][/INDENT]



Note that this still works fine on the older (out-of-date) 13.04 system, and it's worked just fine on the current 14.04 system up through three days ago.  I didn't use it for a few days, then today, when I turned on the client device and coaxed it to do the network boot, the problem showed up.

Now, when I attempt to boot the client machine, things go just fine (the NFS file system mounts while the Linux kernel on the client is starting, "/bin/busybox" loads and reads "/etc/inittab", and so forth, and everything is fine until it tries to access "/dev/null" while busybox processes the "inittab" file.  The NFS server reports that "/dev/null" does not exist.  Then it reports that "/dev/ttyS0" does not exist.  In fact, nothing in "/dev" exists.  All the other files under "/buildroot-nfs" show up, but the NFS server claims that anything under "/dev" (aka "/buildroot-nfs/dev" and "/usr/local/exports/buildroot-nfs/dev") is not there.  I've confirmed this using a Wireshark packet capture.  The console output now looks like:

[INDENT][FONT=lucida console]...
TCP cubic registered[/FONT][/INDENT]
[INDENT][FONT=lucida console]NET: Registered protocol family 17[/FONT][/INDENT]
[INDENT][FONT=lucida console]Registering the dns_resolver key type[/FONT][/INDENT]
[INDENT][FONT=lucida console]IP-Config: Complete:[/FONT][/INDENT]
[INDENT][FONT=lucida console]     device=eth0, addr=172.16.96.4, mask=255.255.254.0, gw=172.16.96.1,[/FONT][/INDENT]
[INDENT][FONT=lucida console]     host=gs1011, domain=, nis-domain=(none),[/FONT][/INDENT]
[INDENT][FONT=lucida console]     bootserver=172.16.96.1, rootserver=172.16.96.1, rootpath=[/FONT][/INDENT]
[INDENT][FONT=lucida console]VFS: Mounted root (nfs filesystem) on device 0:12.[/FONT][/INDENT]
[INDENT][FONT=lucida console]Freeing unused kernel memory: 144k init[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/null: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/null: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/null: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/null: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/null: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/null: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]Starting logging: start-stop-daemon: open pidfile /var/run/syslogd.pid: Not a directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]start-stop-daemon: open pidfile /var/run/klogd.pid: Not a directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]OK[/FONT][/INDENT]
[INDENT][FONT=lucida console]Starting network...[/FONT][/INDENT]
[INDENT][FONT=lucida console]ip: RTNETLINK answers: File exists[/FONT][/INDENT]
[INDENT][FONT=lucida console]ifup: can't open '/var/run/ifstate': Not a directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/ttyS0: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/ttyS0: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/ttyS0: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/ttyS0: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/ttyS0: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/ttyS0: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/ttyS0: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/ttyS0: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/ttyS0: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/ttyS0: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/ttyS0: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/ttyS0: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/ttyS0: No such file or directory[/FONT][/INDENT]
[INDENT][FONT=lucida console]can't open /dev/ttyS0: No such file or directory[/FONT][/INDENT]


On the other hand, nothing shows up in the syslog on the host about this.

I can't change the Linux kernel on the client system to create "/dev" at start-up; it would require re-certification if I change it which is cost-prohibitive.  The exported file system tree has not changed, the boot firmware on the client has not changed, and my NFS configuration has not changed for months.

My guess is that a recent update (applied today) has changed some sort of security policy that prevents the NFS server from exporting any device nodes (from "/dev" or anywhere else).

I would very much appreciate any information or suggestions to that might help solve this problem.

**Host System Identification:**

[LIST]
[*]Ubuntu 14.04 Desktop (amd64)
[*]Updates applied as of noon on 10/3/2014
[/LIST]
[INDENT][FONT=lucida console]$ uname -a
Linux gorgon 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
$[/FONT][/INDENT]

[LIST]
[*]Packages nfs-common, nfs-kernel-server, isc-dhcp-server, tftpd-hpa, and many others installed.
[/LIST]

---

### Post by TheFu on 2014-10-04
Just had to comment - don't have any idea about a solution.
I always thought that /dev was like /proc - a created file system that had to be made per-machine.
Let me check the documentation ... [http://www.pathname.com/fhs/pub/fhs-2.3.html#DEVDEVICEFILES](http://www.pathname.com/fhs/pub/fhs-2.3.html#DEVDEVICEFILES)

So - /dev is for devices, NOT development.

I couldn't find anything in the FHS docs which state that /dev is not shareable. I really expected it to be like /var.
I did find something that says /dev must be located on / - the partition - so that devices are available at boot time.  Perhaps networking isn't up soon enough for NFS to work?  That is where I'd research.

---

### Post by daniel-glasser on 2014-10-06
> **TheFu said:**
> Just had to comment - don't have any idea about a solution.
I always thought that /dev was like /proc - a created file system that had to be made per-machine.
Let me check the documentation ... [http://www.pathname.com/fhs/pub/fhs-2.3.html#DEVDEVICEFILES](http://www.pathname.com/fhs/pub/fhs-2.3.html#DEVDEVICEFILES)


In the ancient past, "/dev" was always a normal directory, not a mount point, and the device nodes were created via "mknod" commands (either in a script or at the console) and persisted between boots unless removed.  This is true for Unix, and used to be for Linux.  On embedded systems, it's not uncommon for this still to be the case.  The kernel we've got for our device is less old than a lot of the ones I've had to work with (3.0.4 rather than 2.6.12), but has been configured without devfs or any of the other dynamic /dev populating mechanisms that have been introduced since the 7th Edition Unix days (which is where I first started playing with Unix).  Our FS is in NOR Flash, normally, so this works well.  The NFS mount is for a "development" version of the root file system that supports such interesting things as compiling and linking, which are not available or desired in the production FS.  We are required to build a particular program on the platform with a native toolchain in order to maintain FIPS certification for the version of OpenSSL we're using, thus my use of the term "development file system".

---

### Post by daniel-glasser on 2014-10-06
After a bit more hair pulling, I solved the problem, and it can be attributed to user error and lack of coordination.

It appears that the problem I have been having is due to a collision in the "fsid" value between two entries.  I am not the only user of the Ubuntu host, though I set it up to begin with, and have been doing all my NFS exports using files in /etc/exports.d.  Somebody edited "/etc/exports" and added an entry to export something else, and that entry also included the attribute specification "fsid=0", thus causing a world of trouble.  Both exports had "/dev", the one I am using has stuff it it, for the other one, "/dev" is empty.  Both exports are for PowerPC E500v2 based platforms, both were Buildroot generated.  I don't know whether everything was loading from the wrong one, or whether my platform was getting a mix of files, some from "/buildroot-nfs", some from "/home/userx/something/target-fs".  That other user has not tested the export for the latter yet, so didn't encounter anything odd.

I removed the (to me) unexpected entry from "/etc/exports", added a new file to "/etc/exports.d" with a non-conflicting export line, and now my target is able to get at its "/dev" nodes, thus allowing me to do what I need to do.  I've also informed the other user and suggested that I be consulted before changing the system configuration to avoid such issues in the future.

I have seen no complaints logged by NFS in the files under "/var/log" about the conflicting "fsid"s.  I don't know if there is any way to check for conflicts of this sort before starting the NFS server.  I've found nothing so far.

---

### Post by TheFu on 2014-10-06
Two cooks in the kitchen without a strict agreement usually turns out badly.

Before we started using ansible to manage our systems, we used a mediawiki page for each server config and before that we had a physical notebook where we wrote notes for any changes.

Communication is key.

---

