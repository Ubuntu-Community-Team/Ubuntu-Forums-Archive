---
title: "cache open failed when installing"
date: 2007-06-05
forum: General Help
---

### Post by zwacka on 2007-06-05
Just started to really use ubuntu 7.04 yesterday and after i used the synaptic to install virtualbox i get this error message when i try to install any program

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

I tried to just install codecs to watch a movie and now nothing wont work.

---

### Post by taurus on 2007-06-05
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
```

---

### Post by zwacka on 2007-06-05
I did this and it still wont work correctly
```
:~$ sudo dpkg --configure -a
Setting up virtualbox (1.3.2-17408_Debian_etch) ...
-e 
Creating group 'vboxusers'. VM users must be member of that group!

Starting VirtualBox kernel moduleFATAL: Error inserting vboxdrv (/lib/modules/2.6.20-15-generic/misc/vboxdrv.ko): Invalid argument
(modprobe vboxdrv failed)...fail!
invoke-rc.d: initscript virtualbox, action "start" failed.
dpkg: error processing virtualbox (--configure):
 subprocess post-installation script returned error exit status 1
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.132.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

```
I wrote for it to overwrite but this showed after
```
The subnet 172.16.85.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] y

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox
 vmware-player

```

---

### Post by taurus on 2007-06-05
Are you trying to install both virtualbox and vmware-player on your machine?  You can remove both if you wish.

```
sudo aptitude --purge remove vmware-player virtualbox
sudo dpkg --configure -a
sudo aptitude update
```

---

### Post by zwacka on 2007-06-05
everything else installs fine now, thank you so much.
i guess it was just a problem w/ the install of vmware

---

