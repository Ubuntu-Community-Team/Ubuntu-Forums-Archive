---
title: "DRBD Module Compliation How-to"
date: 2007-08-29
forum: General Help
---

### Post by nek on 2007-08-29
I have never gotten the standard Ubuntu DRBD module source to compile. The most common error was: 

[INDENT]mv: missing destination file operand after `drbd_buildtag.c{.new,}' [/INDENT]

This method will use a combination of files from the latest source code at the DRBD web site and the Debian-specific files from the default Ubuntu version.

This procedure was tested using the following software versions:
	Kernel: 2.6.20-15-server
	Ubuntu DRBD package: drbd8-module-source
	DRBD web site: drbd-8.0.5.tar.gz

1. Prepare the system. We have to change the standard Ubuntu shell from dash to bash and install the software needed for module building.

```
root# rm /bin/sh
root# ln –s /bin/bash /bin/sh
root# apt-get install build-essential bison flex 
root# apt-get install drbd8-utils drbd8-module-source
root# apt-get install linux-headers-`uname-r`
```

2. Next we will download the latest tarball VERSION. Check the website ([http://oss.linbit.com/drbd/](http://oss.linbit.com/drbd/)) to get the latest VERSION number. Replace VERSION with the actual version number in the code snippets below.

```
root# cd /usr/src
root# wget http://oss.linbit.com/drbd/8.0/drbd-VERSION.tar.gz
``` 
	
3. Extract the tarballs and rename the Ubuntu one, creating a backup in case something goes wrong later.

```
root# tar zxvf drbd-8.VERSION.tar.gz
root# tar zxvf drbd8.tar.gz
root# mv drbd8.tar.gz drbd8.tar.gz.ORIG
```

4. Next we have to move some files around, do some editing, and create a new tarball that the Debian module-assistant program will use to build and install the DRBD module.

```
root# cd /usr/src/modules/drbd
root# rm –r drbd* Makefile scripts
root# cp –r /usr/src/drbd-VERSION/* .
root# vi /usr/src/modules/drbd/debian/changelog
```
[INDENT]Change the version number inside the parentheses on the first line to reflect the VERSION number above.[/INDENT]
```
root# cd /usr/src
root# tar zcvf drbd8.tar.gz modules/
```

5. Create the module and install it. At the end of this step you will have a Debian package in the /usr/src/ directory that you can install on the other server without having to compile the module again.

```
root# m-a 
```
[INDENT]Choose “SELECT” and hit enter
Choose “drbd8-module” and hit enter
Choose “BUILD”
Choose “NO”  if asked to install or upgrade the selected source package.
Continue the process and install the module when prompted.[/INDENT]
```
root# update-modules
root# modprobe drbd
```

6. Copy the package file to the other server and install it.

```
root# scp /usr/src/drbd8-module-2.6.KERNEL_VERSION_MODULE_VERSION+2.6.20-15.27_i386.deb other-server:/usr/src
root# ssh other-server
root# dpkg -i /usr/src/drbd8-module-2.6.KERNEL_VERSION_MODULE_VERSION+2.6.20-15.27_i386.deb
root# update-modules
root# modprobe drbd

```

That should do it. If you have questions or comments, I'll be happy to respond.

---

### Post by clicker666 on 2007-09-05
Thanks for your work!

This was actually the only article I found that let me successfully create DRBD.  Now if I can just figure out how to get heartbeat and drbd to play nicely with VMware server I'd be a happy man.

---

### Post by nek on 2007-09-05
You're welcome. I've never used VMWare, but if you're interested, I can post my notes for getting an active/passive server setup running. I've been using it for about 8 or 9 months now, and it has worked flawlessly. I use it to control Samba, Apache, BackupPC, Jabber, MySQL, vsFTP, and probably something I've forgotten.

---

### Post by poki on 2007-09-20
Hello,
I just used your article to install DRBD on Ubuntu. Thanks a lot, I really appretiate that.
But during drbd startup I am receiving this error:

**can not open /dev/drbd0: No such device or address**

These were my steps after installation:
- created partition on hdd for data and for metadata
- created block device for DRBD; used:
   **for i in `seq 0 15` ; do mknod -m 0660 /dev/drbd$i b 147 $i; done**
- create my own drbd.conf
   I will attatched my drbd.conf
- I also created the metadata using   **drbdadm create-md r0**
- Then I tried to start DRBD using **/etc/init.d/drbd start**
   and that's where I am receiving the mistake No such device or address

Please could you help me, I really dont know and I am already strugling for two days with this error.
Thanks a lot

_My drbd.conf:_
[COLOR="Blue"]global {
usage-count no;
minor-count 64;
 }

common {
  syncer { rate 10M; }
}

resource r0 {

  protocol C;

  disk {
    on-io-error   detach;
  }

  on ubuntu1 {
    device     /dev/drbd0;
    disk       /dev/sdb1;
    address    10.0.0.1:7788;
    flexible-meta-disk /dev/sdc1;

  }

  on ubuntu2 {
    device    /dev/drbd0;
    disk      /dev/sdb1;
    address   10.0.0.2:7788;
    flexible-meta-disk /dev/sdc1;
  }
}
[/COLOR]

_cat /proc/drbd:_
version: 8.0.6 (api:86/proto:86)
SVN Revision: 3048 build by root@ubuntu1, 2007-09-18 17:36:07

_lsmod | grep drbd:_
drbd                  222972  0
cn                     10528  1 drbd

---

### Post by nek on 2007-09-20
Here are the steps I used. Please let me know if it works for you.

**Introduction**

This is an active/passive setup. The server server_1 is the primary node for the shared services.

This how-to assumes the two hosts are connected via dedicated network adapters using 
[INDENT]a crossover network cable on eth1, [/INDENT]
[INDENT]a crossover or null modem cable on /dev/ttyS1, [/INDENT]
[INDENT]and that file systems (ext3) exist on both disks used for DRBD. [/INDENT]

If file systems do not exist, you must create one after step 7, i.e. from the primary node:

```
root# mkfs.ext3 /dev/drbd0
```

Read through some help resources before getting started. Much can go wrong.
[INDENT][http://www.drbd.org/start.html](http://www.drbd.org/start.html)[/INDENT]
[INDENT][http://linux-ha.org/DRBD](http://linux-ha.org/DRBD)[/INDENT]
[INDENT][http://wiki.linux-ha.org/DataRedundancyByDrbd](http://wiki.linux-ha.org/DataRedundancyByDrbd)[/INDENT]
[INDENT][http://linux-ha.org/Heartbeat](http://linux-ha.org/Heartbeat)[/INDENT]

**Gotchas**

1. If services that heartbeat controls run under any user other than root, make sure that the uid and gid are the same on both nodes. I use LDAP for shared users. 

2. Install services that heartbeat will control only when the node is in active mode. See gotcha 1 above. If the installation script added users and groups, make sure the users and groups have the same uid and gid before installing the software on the other server.

3. I had to add a script, /etc/network/if-up.d/route-del, to keep eth1 from being added to the routing table. If the kernel adds eth1 to the routing table before eth0, the server can not connect to the network.

```
#!/bin/bash
/sbin/route del -net 192.168.1.0 netmask 255.255.255.0 dev eth1
exit 0
```

4. Make sure the network cards used to connect the nodes are running at 1Gb/sec, else synchronization will be terribly slow. I use /etc/ha.d/resource.d/Ethsetup for this:
```
#!/bin/bash
ETHTOOL="/usr/sbin/ethtool"
DEVICE="eth1"
case "$1" in
  start)
    echo "Setting $DEVICE speed to 1 Gb/sec"
    $ETHTOOL -s $DEVICE speed 1000
    ;;
   stop)
    echo "Setting $DEVICE speed to 1 Gb/sec"
    $ETHTOOL -s $DEVICE speed 1000
    ;;
  status)
  $ETHTOOL $DEVICE|grep Speed
   ;;
  *)
    echo "Usage: Ethsetup {start|stop|status}"
    exit 1
    ;; 
esac
exit 0
```

5. Do not allow shared services to start automatically. You also have to check this after running a software update.

```
root# update-rc.d -f init-script-name remove
```

**Build the Module** 
See initial post.

**Configure DRBD and Heartbeat**

1. Edit /etc/fstab and add a similar line (same for both hosts).

```
/dev/drbd0  /raid5  ext3  noauto  0  0
```

2. Edit /etc/drbd.conf. Use same file on both hosts.

```
resource drbd0 {
  protocol C;
  incon-degr-cmd "echo 'DRBD primary inconsistent' | wall ; /etc/init.d/heartbeat stop";
  startup {
    wfc-timeout 30;
    degr-wfc-timeout 180;    # 120 seconds
  }
disk {
on-io-error   detach;
}
net {
}
syncer {
rate 120M;
al-extents 1801;
}
on server_1 {
device     /dev/drbd0;
disk       /dev/sdb1;
address    155.206.125.61:7788;
meta-disk  internal;
}
on server_2 {
device    /dev/drbd0;
disk      /dev/sdb1;
address   155.206.125.62:7788;
meta-disk internal;
}
}

```
3. Execute the following on the primary host.

```
root# drbdadm -- --do-what-I-say primary all
```

4. Test the setup.

Execute the following on the primary host.

```
root# mount /raid5
root# vi /raid5/test
This is a test file.
root# umount /raid5
root# drbdadm secondary all
```

Execute the following on the secondary host.

```
root# drbdadm primary all
root# mount /raid5
root# cat /raid5/test
This is a test file.
```

5. Install heartbeat.

```
root# apt-get install heartbeat
```

6. Configure /etc/ha.d/ha.cf

```
debugfile /var/log/ha-debug
logfile /var/log/ha-log
keepalive 2
deadtime 20
warntime 10
initdead 60
serial  /dev/ttyS1
auto_failback on
node    server_1 server_2
```

7. Configure /etc/ha.d/authkeys

```
auth 1
1 crc
```

8. Configure /etc/ha.d/haresources

This is the most difficult step in the entire process. If an init script returns anything other than 0, heartbeat will fail and give up its resources. This means that while trying to takeover the resources, for example, one of the services already has a pid file, the script will return 1, heartbeat will fail and give up all of the resources by stopping the services. This will leave you with both nodes confused and none of the shared services running.

The services in caps in the example haresources are the ones that gave me problems. Rather than rewrite the scripts in /etc/init.d, I put scripts in /etc/ha.d/resource.d/, i.e. BACKUPPC, that start and stop the services.

/etc/ha.d/haresources example:
```
server_1 Ethsetup drbddisk::drbd0 Filesystem::/dev/drbd0::/raid5::ext3 IPaddr::155.206.125.70/24/eth0 SLAPD samba mysql apache2 BACKUPPC VSFTPD JABBER
```

/etc/ha.d/resource.d/BACKUPPC:
```
#!/bin/bash
SCRIPT="/etc/init.d/backuppc"
NAME="BACKUPPC"
TEST=`ps -u backuppc|grep BackupPC`
RUNDIR="/var/run/backuppc"
case "$1" in
 start)
 if [ -n "$TEST" ]; then
      $SCRIPT stop
    fi
    sleep 1
    if [ -d "$RUNDIR" ]; then
      chown backuppc:backuppc /var/run/backuppc
    fi
    $SCRIPT start
    ;;
  stop)
   $SCRIPT stop
    ;;
  *)
    echo "Usage: $NAME {start|stop}"
    exit 1
    ;; 
esac
exit 0
```

---

### Post by poki on 2007-09-21
Hello,
actually I didn't start to configure Heartbeat. First I want to have functional DRBD. I am still receiving the same error **can not open /dev/drbd0: No such device or address**.

Do I have to create block device using **mknod /dev/drbd0 b 147 0**?

This is my idea how it is suppose to work, correct me please if I am wrong.
- Install DRBD - I did this using your article
- modprobe drbd
- edit drbd.conf
- mknod /dev/drbd0 b 147 0, this will create block device for DRBD
- drbdadm create-md r0, this will manually create metadata.
- NOW start DRBD using: **/etc/init.d/drbd start** !!! Here I am receiving the error
- mkfs.ext3 /dev/drbd0
- mount the FS

Are the steps correct? Or I dont have to create block device? I didnt see in your last posting that you were creating the block device.
How to verifie installation of my DRBD?

Oh, I really appretiate your help, I hope we will find the problem.

---

### Post by nek on 2007-09-22
> Do I have to create block device using mknod /dev/drbd0 b 147 0?

I didn't. Note that I already had an existing file system on my disk. However, if you do not have an existing file system, that will work as well. Read the Introduction part of my post.

> How to verifie installation of my DRBD?

See step 4.Test the setup under Configure DRBD and Heartbeat. Of course, you can only test it if you can mount the DRBD disk.

---

