---
title: "Ethernet not working on T22"
date: 2007-05-29
forum: General Help
---

### Post by psrivats on 2007-05-29
I installed Fiesty on my IBM T22 (2647-AEU) and I am not able to get the ethernet working. I have the Intel 10/100 Ethernet Mini-PCI Adapter with 56K modem.

**Output of dmesg:**
 
$ dmesg | grep eth
[   14.196308] e100: eth0: e100_probe: addr 0xe8120000, irq 11, MAC addr 00:03:47:B7:FD:D5
[   66.376000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2223.828000] e100: eth0: e100_probe: addr 0xe8120000, irq 11, MAC addr 00:03:47:B7:FD:D5
[ 2224.316000] ADDRCONF(NETDEV_UP): eth0: link is not ready

Can anyone point me how to get this working? 

Apart from this error, my installation went really well, absolutely no issues whatsover w.r.t sound or display.

---

### Post by psrivats on 2007-05-29
Anyone?

---

### Post by psrivats on 2007-05-31
Bump :(

---

### Post by Talon2 on 2007-05-31
I wish I could help but my T23 uses a different card than yours.  Mine is the Intel ethernet daughter card and I think yours is 3Com mini pci combo.

Maybe this site could help you:

[http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

---

