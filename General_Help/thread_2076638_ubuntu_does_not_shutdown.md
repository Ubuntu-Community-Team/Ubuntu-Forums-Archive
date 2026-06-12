---
title: "ubuntu does not shutdown"
date: 2012-10-26
forum: General Help
---

### Post by mordox on 2012-10-26
I have a freshly installed ubuntu 12.10 on a HP DM4 laptop.

I saw a few times the following error "mount / is busy" and added a few lines in the umountfs script. These were

killall -9 plymouthd
killall -9 dhclient
killall -9 /sbin/plymouthd
killall -9 /sbin/dhclient
killall -9 dnsmasq
killall -9 /usr/sbin/dnsmasq


ps -Af > /a/ps
lsof > /a/lsof
sync && sleep 30 && sync

However even after this when I shutdown the system via the menu it does not shutdown. Screenshots are attached. It stayed in the same state for atleast 20min.

[ATTACH]226152[/ATTACH]

[ATTACH]226153[/ATTACH]

---

