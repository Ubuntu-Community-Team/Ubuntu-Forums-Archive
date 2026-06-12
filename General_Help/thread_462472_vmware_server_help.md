---
title: "vmware server help"
date: 2007-06-02
forum: General Help
---

### Post by nami on 2007-06-02
i've installed vmware server 1.0.3 on 7.04, but the internet is not working.  how do i get it to work?  when i installed 1.0.2 on 6.10 the internet worked "out of the box" so to speak.

---

### Post by veloce on 2007-06-03
> **nami said:**
> i've installed vmware server 1.0.3 on 7.04, but the internet is not working.  how do i get it to work?  when i installed 1.0.2 on 6.10 the internet worked "out of the box" so to speak.

Depends how you installed.  Did you use the install from the repository?

If so, you get the standard vmnet setup, otherwise I don't think any vmnets are installed.

---

### Post by nami on 2007-06-03
> **veloce said:**
> Depends how you installed.  Did you use the install from the repository?

If so, you get the standard vmnet setup, otherwise I don't think any vmnets are installed.

I installed it using this guide:
[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

How do I install it using the repository?

---

### Post by veloce on 2007-06-04
> **nami said:**
> I installed it using this guide:
[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

How do I install it using the repository?

The third comment on that howto has the instructions.  Or:
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

However, since you have it installed, leave it until you next do an upgrade of the kernel.

To check and alter the network settings, run the network config script:

vmware-config-network.pl

Easiest (though least secure) way of getting the internet working is to use bridged networking.

If that's enabled in vmware, then all you need to do is add a network card connected to the bridged network to your vm.

---

### Post by nami on 2007-06-04
> **veloce said:**
> The third comment on that howto has the instructions.  Or:
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

However, since you have it installed, leave it until you next do an upgrade of the kernel.

To check and alter the network settings, run the network config script:

vmware-config-network.pl

Easiest (though least secure) way of getting the internet working is to use bridged networking.

If that's enabled in vmware, then all you need to do is add a network card connected to the bridged network to your vm.

When the the kernal upgrade be available and will it fix vmware server?

anyway I tried>  vmware-config-network.pl and it gave me this, i am reluctant to setup the network because I don't know what to set it up as???

the output i got was this.

> nami@nami-desktop:~$ sudo vmware-config-network.pl
Password:
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

This program previously created the file /dev/parport0, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport1, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport2, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport3, and was about to remove
it.  Somebody else apparently did it already.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] 
nami@nami-desktop:~$

---

### Post by veloce on 2007-06-04
> **nami said:**
> When the the kernal upgrade be available and will it fix vmware server?

anyway I tried and it gave me this, i am reluctant to setup the network because I don't know what to set it up as???

the output i got was this.

Kernel upgrades always "break" vmware server - there are some bits that need to be compiled specifically for the kernel being used.

If you want your vms to access the internet or other machines on your network then you have to set up virtual networking.

It is true that it may not be clear what you want.  If your host is connected to a network that provides a gateway to the internet then you want to use **bridged** networking. If your machine uses a modem of any description then use **nat** networking. If you don't want to access the internet but just want to share files with the host machine, then use** host-only** networking.
[LIST]
[*]Turn off or leave off all the ones you don't use.
[*]Use defaults where ever possible.
[/LIST]

---

