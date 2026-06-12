---
title: "problems installing vmware-player"
date: 2007-10-03
forum: General Help
---

### Post by stubish on 2007-10-03
checked a few other threads and nothing came up for me. 

So I enter: sudo apt-get install vmware-player

and this is the return (not including the liscence splash screen).

*******************************************************
stuart@Darkone:~$ sudo apt-get remove --purge vmware-player
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  vmware-player*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 32.1MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 179016 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done
Purging configuration files for vmware-player ...
stuart@Darkone:~$ clear

stuart@Darkone:~$ sudo apt-get install vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  vmware-player
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/11.9MB of archives.
After unpacking, 32.1MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package vmware-player.
(Reading database ... 178609 files and directories currently installed.)
Unpacking vmware-player (from .../vmware-player_1.0.2-2_i386.deb) ...
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.109.0/255.255.255.0 appears to be unused.

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.215.0/255.255.255.0 appears to be unused.

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
stuart@Darkone:~$ 
**************************************************

I'm pretty new at this linux stuff, so please be gentle.

Thanks

---

### Post by stubish on 2007-10-04
is this not the right place to post?

---

