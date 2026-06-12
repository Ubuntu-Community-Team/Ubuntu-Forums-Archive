---
title: "Ubuntu on VMware"
date: 2008-05-30
forum: General Help
---

### Post by andyoww on 2008-05-30
OK
Here's the problem.

Ubuntu was running on VMware (host Server 2003).  Everything was fine until the partition I had created just for this VM ran out of space.

I moved the VM to another partition with more space (the entire folder on the host machine).

I opened the new location in VMware after removing the old one from the inventory.

I have 2 other VMs (NT4 & 2003 server) that work fine.

This one for some reason will not connect to the network.

If I try to ping it's own IP (192.168.10.19), the pings are successful.

If I try to ping anything else on the network, it gives back:
192.168.10.19 destination host unreachable

My thoughts are Ubuntu hasn't tried to use the "new" network card, but everything I try will not allow me to connect.

If I switch this to DCHP, it will get an IP from the server (192.168.10.26), but the same things happen.

I have looked at the arp cache and it says:
192.168.10.26 at <incomplete> on eth0

I'm really having a hard time finding any info on this and would appreciate any help.

I'm not sure if this is the correct category, please move it if it's not.

Ubuntu server (no GUI) 6.10
Thanks,
Jeff

---

### Post by andyoww on 2008-05-30
I just pinged that box from another client (XP).

the request timed out, but when I looked at the arp cache on the XP, it came back with the correct MAC.

It seems as though I'm missing someting very easy!

---

### Post by andyoww on 2008-05-30
And the Ubuntu's arp shows the ip of the XP box.

---

### Post by andyoww on 2008-06-02
Well I got it working.

I had to reboot the host machine.  I hadn't had a chance to do it yet as we had users on it, but now it works.

---

