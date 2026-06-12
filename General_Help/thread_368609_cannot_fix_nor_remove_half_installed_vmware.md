---
title: "cannot fix nor remove half installed vmware"
date: 2007-02-23
forum: General Help
---

### Post by dacxjo on 2007-02-23
A few days ago, I tried to install vmware from their site. Things scrolled by very quickly, but the gist is that the installation somehow failed, but the icons for VMware player and VMware Workstation have appeared in my menu (Applications -> System Tools ->) though they are non-functional.

The final errors said something about not being able to create .desktop icons and something about not being able to compile for my kernel (default stock kernel for Edgy with automatic updates applied).

I tried to use their uninstaller, which failed.

For other reasons, I installed Automatix and noticed that they had a VMware option, so I tried to install from there, hoping it would simply install a good working version over the old version. It failed with similar errors, telling me that it wants to write over some files, and then giving me the same errors as the previous installation.

Trying to uninstall from Automatix was equally unsuccessful.

Now, whenever I apt-get or use Automatix to try to install something new, it tries to complete the vmware installation and configuration. How can I stop this behavior, first of all, and second of all, is there any way to cleanly remove the partially installed VMware?

Thanks

---

### Post by taurus on 2007-02-23
What happens when you run these commands from a terminal?

```
sudo aptitude --purge remove vmware
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by jackrobinson on 2007-02-23
The vmware-player package in Ubuntu Multiverse is broken and the package maintainer has done nothing to fix it in months.
do the following from terminal:
```
sudo rm -f /var/lib/dpkg/info/vmware-player.postrm
sudo rm -f /var/lib/dpkg/info/vmware-player.prerm
sudo apt-get remove vmware-player
```

---

### Post by dacxjo on 2007-02-23
> **taurus said:**
> What happens when you run these commands from a terminal?

```
sudo aptitude --purge remove vmware
sudo aptitude update
sudo aptitude upgrade
```

Thanks for the quick reply. 

Unfortunately, that didn't remove it. Here is the output, which is basically what I get when I try to do anything with apt-get, synaptic, or Automatix.

> 
$ sudo aptitude --purge remove vmware
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find package "vmware".  However, the following
packages contain "vmware" in their name:
  vmware-player vmware-player-kernel-modules-2.6.15-23 vmware-player-kernel-modules-2.6.17-10 
  vmware-player-kernel-modules-2.6.17-11 vmware-player-kernel-source vmware-player-kernel-modules 
  xserver-xorg-video-vmware 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.8.0/255.255.255.0 appears to be unused.

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

The subnet 172.16.237.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
VMware Player is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.145.0/255.255.255.0 appears to be unused.

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


The subnet 192.168.17.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 
The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 


Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
VMware Player is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player


---

### Post by taurus on 2007-02-23
```

sudo aptitude --purge remove vmware-player
sudo aptitude update
sudo aptitude upgrade

```

---

### Post by dacxjo on 2007-02-23
> **jackrobinson said:**
> The vmware-player package in Ubuntu Multiverse is broken and the package maintainer has done nothing to fix it in months.
do the following from terminal:
```
sudo rm -f /var/lib/dpkg/info/vmware-player.postrm
sudo rm -f /var/lib/dpkg/info/vmware-player.prerm
sudo apt-get remove vmware-player
```


Thank you! That did stop the strange apt-get behavior and it also removed VMware-player.

VMware Workstation still appears in the menus, though. I need to figure out how to remove it as well. Thank you!

---

### Post by taurus on 2007-02-24
Try

```
sudo aptitude --purge remove vmware-player
```

---

### Post by jackrobinson on 2007-02-24
> **taurus said:**
> Try

```
sudo aptitude --purge remove vmware-player
```

The OP installed Vmware Workstation from the vmware site. Read his first post. He is asking how he can remove Vmware Workstation now that he has successfully removed vmware-player.

---

### Post by skivikko on 2007-02-25
Hi,
you should remove everything from /etc/vmware 

rm /etc/vmware/state/locations
and so on...
rmdir /etc/vmware/state
rmdir /etc/vmware



after that you should be able to re-install vmware workstation, be sure that you don't go with the full path but like this

cd /what_ever_the_installer_location_is
-->sudo vmware-installer.pl

Hope this works, did it for me :)

---

### Post by dacxjo on 2007-02-27
Unfortunately, that made it worse. Now I have a broken vmware player and workstation in the menu, and the reinstall failed. Also, the uninstaller doesn't seem to work at all. It says it successfully uninstalls, but it still appears in the menu and there area still lots of vmware files in /usr/bin and other places.

Thank you for trying. Anyone else have a suggestion? 

At this point, I've given up on any form of VMware, and just want to remove it completely from my system.

---

### Post by zvacet on 2007-02-27
From your last post I belive that you know where the vmware files are.Do this```
sudo -i
```
and go to the folder with vm ware files and
```
rm -r filename
```
do this with every folder containing vmware files.

---

### Post by jallen13 on 2008-03-20
Just what I needed.. Thank you!!!!

---

