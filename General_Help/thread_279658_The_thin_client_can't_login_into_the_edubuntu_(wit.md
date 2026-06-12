---
title: "The thin client can't login into the edubuntu (with ltsp server)."
date: 2006-10-18
forum: General Help
---

### Post by sshgz on 2006-10-18
I have installed edubuntu 6.06 (with ltsp server) on the vmware 5.5.

Now the thin client (virtual pc of vmware) can't login into the edubuntu.

Please see the attachment.

My edubuntu server ip is "192.168.182.131", but the error shows that the rootserver is "192.168.182.254". Why?

I am waiting for your help.

Thanks.

---

### Post by Tortanick on 2006-10-22
As a guess I'd say the problem is rootpath:

Try setting it to / or /dev/hda/ 

And I have no idea how you do that.

---

### Post by crmanski on 2006-10-29
I think that the problem that you are having is due to the DHCP config. It is telling your client that the ltsp server is 192.168.182.254.

I would look at the DHCP config file and make sure that the IP addresses in that file are correct.This page has information on edited the config file about 2/3rds of the way down the page...
[http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted)

> **sshgz said:**
> I have installed edubuntu 6.06 (with ltsp server) on the vmware 5.5.

Now the thin client (virtual pc of vmware) can't login into the edubuntu.

Please see the attachment.

My edubuntu server ip is "192.168.182.131", but the error shows that the rootserver is "192.168.182.254". Why?

I am waiting for your help.

Thanks.

---

### Post by sshgz on 2006-10-30
Thanks crmanski.

I am sure that the DHCP config file is right.

---

### Post by crmanski on 2006-10-30
> **sshgz said:**
> Thanks crmanski.

I am sure that the DHCP config file is right.

From looking at the screenshot it seems to be the case. Your DHCP server is 192.168.182.131, but it is telling the client that it is 192.168.182.254. This is determined by the DHCP server's config. you could try adding this option to the DHCP config...

```
next-server 192.168.182.131;

```

---

### Post by sshgz on 2006-10-31
Thanks crmanski.

---

### Post by Morgon123 on 2007-01-11
I got the same problem: My server is on 192.168.1.200 but it always says rootserver: 0.0.0.0. Adding the next-server-line to dhcp.conf didn't help anything...

---

### Post by crmanski on 2007-01-11
Silly question. Did you restart the dhcp service after adding the next-server option?
If you post your dhcp.conf file. I'll take a look.

---

### Post by stefandebacker on 2007-02-04
I would like to use thin clients on my network at the school where I work

For this I would like to use edubuntu

At home, everything works just fine, but when I tried to change the range of my dhcp of the thin clients, the clients can't log in anymore.
Standard the range is 192.168.0.1 with subnetmask 255.255.255.0

I want the range 192.168.100.1 (subnetmask 255.255.255.0) because the range192.168.0.1 is already taken in my network.

The manual says I have to change the following:

/etc/network/interfaces
 >        # The loopback network interface
        auto lo
        iface lo inet loopback

        # The primary network interface
        auto eth0
        iface eth0 inet static
    address 192.168.1.14
    netmask 255.255.240.0
    network 192.168.0.0
    broadcast 192.168.15.255

        auto eth1
        iface eth1 inet static
            address 192.168.100.254
            netmask 255.255.255.0
            network 192.168.100.0
            broadcast 192.168.100.255


/etc/ltsp/dhcpd.conf
>         authoritative;

        subnet 192.168.100.0 netmask 255.255.255.0 {
          range 192.168.100.20 192.168.100.250;
          option domain-name "example.com";
          option domain-name-servers 192.168.100.1;
          option broadcast-address 192.168.100.255;
          option routers 192.168.100.1;
          option subnet-mask 255.255.255.0;
          if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
            filename "/ltsp/i386/pxelinux.0";
          }
          else{
            filename "/ltsp/i386/nbi.img";
          }
          option root-path "/opt/ltsp/i386";
        }
The thin client boots, I get the login screen, but i can't login anymore.

Does anyone know what went wrong, or what else I have to do to make things work again?

Thanks for your support!

---

### Post by crmanski on 2007-02-05
When you changed the IP of the server did you follow the instructions on the bottom of this wiki page?
[https://help.ubuntu.com/community/HowToCookEdubuntu/Chapters/LTSPManagement](https://help.ubuntu.com/community/HowToCookEdubuntu/Chapters/LTSPManagement)

---

### Post by stefandebacker on 2007-02-05
:(  No I didn't.

But now that you told me... :guitar: SUPER IT WORKS!!

Thanks a lot, crmanski!!! You really saved my day.

---

