---
title: "VMware problem installing now can't uninstall"
date: 2007-03-02
forum: General Help
---

### Post by helliewm on 2007-03-02
I have not been able to install VMWARE by Automatix now I can't uninstall it either nor can I download any other software from the repositories. I have run dpkg --configure -a from the command line and that does not solve the problem either.

See here: 

helen@helen-laptop:~$ sudo dpkg --configure -a
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.220.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] y

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.54.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] y

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
helen@helen-laptop:~$ 

Anyone any ideas, what to do next?

Helen

---

### Post by zvacet on 2007-03-02
```
sudo -i
```
In usr/bin you will find something like  vmware-uninstall
```
root@localhost#./vmware-uninstal
```
Of course you will put right name of vmware file.After that you can chek home,etc.etc/init.d,tmp just to be sure that no vmwarer file are left.If you find some file remove it with ```
rm -r filename
```
but you have to be root
```
sudo -i
```

---

### Post by helliewm on 2007-03-02
Thanks sorted now after 2 hours searching the forum. I found the same advice hidden in another thread. 

It seems to be a common problem with vmware but quite hard to search the forum as people label/explain the problem differently.

Anyway many thanks, your advice is spot on for anyone else reading this thread.

Helen

---

### Post by zvacet on 2007-03-03
Most important thing is that you solve your problem.Btw,I think that vmware server is better choice,but that just my opinion.

---

