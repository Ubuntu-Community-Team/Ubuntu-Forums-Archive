---
title: "Problem sharing an internet connection with DHCP"
date: 2006-10-28
forum: General Help
---

### Post by Pulse on 2006-10-28
I'm trying to share an internet connection with an XP box but I've run into a roadblock.  When trying to start dhcp I get a generic "dhcp cannot start" error, and the following output in syslog: ```
Oct 28 19:12:31 localhost dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Oct 28 19:12:31 localhost dhcpd: All rights reserved.
Oct 28 19:12:31 localhost dhcpd: 
Oct 28 19:12:31 localhost dhcpd: Please contribute if you find this software useful.
Oct 28 19:12:31 localhost dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Oct 28 19:12:31 localhost dhcpd: 
Oct 28 19:12:31 localhost dhcpd: No subnet declaration for eth1 (209.145.114.249).
Oct 28 19:12:31 localhost dhcpd: Please write a subnet declaration in your dhcpd.conf file for the
Oct 28 19:12:31 localhost dhcpd: network segment to which interface eth1 is attached.
Oct 28 19:12:31 localhost dhcpd: exiting.
```

How do I go about declaring a subnet for eth1?  There don't seem to be any docs related to this and dhcpd.conf doesn't mention specific interfaces anywhere.  etih1 is the device used to onnect to the internet, by the way.

Edit: I probably should've put this in the networking forum.  Could a mod move it there please?

---

### Post by Pulse on 2006-10-29
After doing a bit a research, I have found that Firestarter is supposed to do this for me.  However, telling Firestarter to make a DHCP config in either the wizard of the preferences menu does not generate a new dhcpd.conf like it is supposed to.

---

### Post by jaclayton on 2006-11-07
I'm having the same problem here - how did you solve yours?

---

### Post by Iowan on 2006-11-07
Simplest solution may be to edit the **dhcpd.conf** file manually.  I'll check my server when I get home to see if it reveals any interesting/useful information.  BTW, have you checked **man dhcpd.conf**?

---

### Post by Iowan on 2006-11-07
Inside my **/etc/dhcp3/dhcpd.conf** file is a section *similar* to:```
subnet 209.145.114.0 netmask 255.255.255.224 {
  range 209.145.114.200 209.145.114.248;
  option domain-name "pulse";
  option routers 209.145.114.1;
}

```
I took the liberty of making it look like yours might.
There are about 2000 lines of info in **man dhcpd.conf**, and samples in the **/etc/dhcp3/dhcpd.conf** file.  I did a:```
cp /etc/dhcp3/dhcpd.conf /etc/dhcp3/dhcpd.conf.original
```
before I started editing - so I'd have the original to reference.

---

