---
title: "Gutsy in vmware, with nis/nfs users, having authentication trouble"
date: 2007-11-29
forum: General Help
---

### Post by deej1976 on 2007-11-29
Hi forum,

I've installed ubuntu 7.10 inside vwmare server 1.0.4 build-56528 running on ubuntu 7.10 ( for testing purposes ).

This is then been plugged into a nis/nfs Sun Solaris enviroment.

vmware server is using a NAT network connection and ubuntu 7.10 guest is using dhcp ( non-roaming ) to obtain an IP address.

The problem that I'm getting is that NIS users cannot log into the machine via gdm or ssh ( openssh-server installed ), local users are ok. sudo su - nis_userid results in the following message "su: Authentication service cannot retrieve authentication info (ignored). However the su successed and the users homearea is mounted correctly. I have found that ypcat passwd.adjunct.byname nis map is not found, all other maps are present though.

If I change the IP address to a vmware bridged network and a statical configured address in the host that is on the same network as the host everything works correctly. switching back to vmware NAT and dhcp (non-roaming) causes the problem again.

The setup is as follows:

Extra packages installed are:
nis ( with domainname being set during configuration )
portmap
nfs-common
nfs-client
autofs
resolvconf

The following files are edited:
/etc/hosts - ipaddresses and names of nis-slaves are added.

/etc/yp.conf - list of domain [name] server [nis-slave] are added to stop broadcast

/etc/resolv.conf - domain, search and nameservers are add with resolvconf keeping them between reboots.

/etc/auto.master - following entry added
	/home   yp:auto.home --timeout=60

/etc/nsswitch.conf - is changed to reflect nis environment like so:

passwd:     nis files
shadow:     nis files
group:      nis files
hosts:      nis dns [NOTFOUND=return] files
bootparams: nis [NOTFOUND=return] files
ethers:     nis files
netmasks:   nis files
networks:   nis files
protocols:  nis
rpc:        nis files
services:   nis files
netgroup:   nis files
publickey:  nis
# automount:  nis files
aliases:    nis files

Have tried adding +(:'s) required to /etc/passwd /etc/group and /etc/shadow as found in various NIS setup howto's.

Does anyone have an ideas what is causing this problem?

Regards

---

### Post by deej1976 on 2007-11-30
Using wireshark on Gutsy and snoop on the Solaris NIS server found that connections from the vmware gutsy were come though above port 1024. Solaris will not give up the passwd map for unprocess that is not below 1024.

To fix this problem with vmware server you need  to add the following lines to nat.conf which is in the /etc/vmware/vmnet8/nat directory:

[privilegedUDP]
autodetect=1

[privilegedTCP]
autodetect=1

This allows connection below 1024.

We can successfully login via GDM, su - and ssh.

Regards

---

