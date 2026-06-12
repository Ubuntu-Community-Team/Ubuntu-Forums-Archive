---
title: "Creating a static pre-configured IP on a LiveCD"
date: 2008-06-24
forum: General Help
---

### Post by rcastley on 2008-06-24
Hi All,

I am trying to create a LiveCD (using the excellent Live CD From Scratch documentation).

All is going very well but I have one requirement that I can't figure out how to do.

My requirement is to have the LiveCD boot up and eth0 to be configured via DHCP and eth1 to use a preconfigured static IP.  I tried edting /etc/network/interfaces but this gets overridden when the LiveCD boots.

I can't find anywhere how to enable this.

I would like this requirement as I would like to have a DHCP server assigned to eth1 and until I can make eth1 have a static IP DHCP server fails to start.  Once the LiveCD is booted I can obviously make the changes and all is OK but I would like this to all work unattended.

If anyone out there has any suggestions etc. they would be very, very welcome :-)

Thank you,

- Robert

---

### Post by rcastley on 2008-06-25
I think I have discovered how to do this:

1) Edit accordingly /usr/share/initramfs-tools/scripts/casper-bottom/23networking

2) Run update-initramfs -u -k $version 

- Robert

---

