---
title: "Installing vmware-player in Ubuntu Dapper fails"
date: 2008-05-17
forum: General Help
---

### Post by uba704 on 2008-05-17
Hi,

I have a new install of Ubuntu Dapper 6.06.2 LTS and am trying to install vmware-player but "apt-get install vmware-player" fails. It seems like it install kernel modules for 2.6.15-29, but I am running 2.6.15-51. Maybe I can compile my own kernel modules for 2.6.15-51, or what do you think is the best solution (I do not want to upgrade to Ubuntu 8.04 at this point)? Thanks for any advice!

# uname -a
Linux myhost 2.6.15-51-386 #1 PREEMPT Tue Feb 12 16:52:52 UTC 2008 i686 GNU/Linux

# apt-get install vmware-player
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libcroco3 librsvg2-2 libssl0.9.7 vmware-player-kernel-modules vmware-player-kernel-modules-2.6.15-29
Suggested packages:
  librsvg2-bin
The following NEW packages will be installed:
  libcroco3 librsvg2-2 libssl0.9.7 vmware-player vmware-player-kernel-modules vmware-player-kernel-modules-2.6.15-29
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.4MB of archives.
After unpacking 38.3MB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper-updates/restricted vmware-player-kernel-modules-2.6.15-29 2.6.15.11-14 [166kB]
Get:2 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper-updates/multiverse vmware-player-kernel-modules 2.6.15.11-14 [7258B]
Get:3 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper/main libcroco3 0.6.1-1build1 [106kB]
Get:4 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper/main librsvg2-2 2.14.4-0ubuntu1 [121kB]
Get:5 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper-updates/universe libssl0.9.7 0.9.7g-5ubuntu1.1 [2178kB]
Get:6 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper/multiverse vmware-player 1.0.1-4 [11.8MB]
Fetched 14.4MB in 2s (6988kB/s)
Preconfiguring packages ...
Selecting previously deselected package vmware-player-kernel-modules-2.6.15-29.
(Reading database ... 148569 files and directories currently installed.)
Unpacking vmware-player-kernel-modules-2.6.15-29 (from .../vmware-player-kernel-modules-2.6.15-29_2.6.15.11-14_i386.deb) ...
Selecting previously deselected package vmware-player-kernel-modules.
Unpacking vmware-player-kernel-modules (from .../vmware-player-kernel-modules_2.6.15.11-14_all.deb) ...
Selecting previously deselected package libcroco3.
Unpacking libcroco3 (from .../libcroco3_0.6.1-1build1_i386.deb) ...
Selecting previously deselected package librsvg2-2.
Unpacking librsvg2-2 (from .../librsvg2-2_2.14.4-0ubuntu1_i386.deb) ...
Selecting previously deselected package libssl0.9.7.
Unpacking libssl0.9.7 (from .../libssl0.9.7_0.9.7g-5ubuntu1.1_i386.deb) ...
Selecting previously deselected package vmware-player.
Unpacking vmware-player (from .../vmware-player_1.0.1-4_i386.deb) ...
Setting up vmware-player-kernel-modules-2.6.15-29 (2.6.15.11-14) ...

Setting up vmware-player-kernel-modules (2.6.15.11-14) ...
Setting up libcroco3 (0.6.1-1build1) ...

Setting up librsvg2-2 (2.14.4-0ubuntu1) ...

Setting up libssl0.9.7 (0.9.7g-5ubuntu1.1) ...

Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.57.0/255.255.255.0 appears to be unused.

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.237.0/255.255.255.0 appears to be unused.

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by zvacet on 2008-05-17
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by uba704 on 2008-05-18
Thanks, I tried that, but didn't get much success. Any idea what to try next?

# apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.15-51
The following NEW packages will be installed:
  linux-headers-2.6.15-51 linux-headers-2.6.15-51-386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 7771kB of archives.
After unpacking 79.7MB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper-updates/main linux-headers-2.6.15-51 2.6.15-51.66 [6914kB]
Get:2 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) dapper-updates/main linux-headers-2.6.15-51-386 2.6.15-51.66 [857kB]
Fetched 7771kB in 0s (8339kB/s)
Selecting previously deselected package linux-headers-2.6.15-51.
(Reading database ... 149031 files and directories currently installed.)
Unpacking linux-headers-2.6.15-51 (from .../linux-headers-2.6.15-51_2.6.15-51.66_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-51-386.
Unpacking linux-headers-2.6.15-51-386 (from .../linux-headers-2.6.15-51-386_2.6.15-51.66_i386.deb) ...
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.21.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists.  Overwrite? [yes]

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.18.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-headers-2.6.15-51 (2.6.15-51.66) ...

Setting up linux-headers-2.6.15-51-386 (2.6.15-51.66) ...
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by zvacet on 2008-05-18
I didn´t use it much but you can look in /usr/bin to find out is there package vm-configure (or something somilar to that) and if it is run it from terminal 

```
sudo /usr/bin/package_name
```

it should reconfigure your player and after that you will be able to use it.For me vmware-server is better option,but that is just me.

---

### Post by uba704 on 2008-05-19
When I run /usr/bin/vmware-config-network.pl it does not try to compile the kernel modules for me.

So instead I downloaded vmware player from [www.vmware.com](www.vmware.com) and that one compiled the kernel modules and it seem to work perfectly, so I am happy :)

By the way, what is the main reason why you prefer vmware-server over vmware player? In my case I use vmware player to run Windows 2000 Pro on my desktop and it seem to work good with network etc.

---

