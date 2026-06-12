---
title: "ubuntu desktop freeze"
date: 2020-10-28
forum: General Help
---

### Post by info-tvnr on 2020-10-28
When i using nas (starting) with a script the nas server comes online, but when i use the option sudo mount -a the desktop freeze everywhere.  
using 20.04
fstab below is everything oké
```
/dev/disk/by-uuid/99531098-0cfc-4333-82a3-32b85cbfc247 / ext4 defaults 0 0
/dev/disk/by-uuid/06055912-5774-4d26-999f-180350c0b7bc none swap sw 0 0
/swap.img    none    swap    sw    0    0
/dev/md0 /home ext4 defaults,nofail,discard 0 0
//192.168.178.21/share /home/user/share cifs guest,uid=1000,vers=1.0   0  0
//192.168.178.21/radiotvnr /home/user/tvnr cifs guest,uid=1000,vers=1.0   0  0
//192.168.178.21/usbdiskcopy /home/user/usbcopy cifs guest,uid=1000,vers=1.0   0  0
//192.168.178.21/Muziek /home/user/Muziek cifs guest,uid=1000,vers=1.0   0  0
```

before this was working everywhere. Mounting was not a problem at all. I think it is an network issue where and how can i find this problem ?
I used nordvpn from terminal and it blocked everything locally :| So I wiped nordvpn and used the openvpn in the networkmanager back again. 
Can this be the issue ?
thanks :)

---

### Post by SeijiSensei on 2020-10-28
Is 192.168.171.0/24 local or on the other side of the VPN?

---

### Post by info-tvnr on 2020-10-29
The problem is solved, but it is really rare that a desktop freeze if the network can not reach his goal (maps etc.) and even mine router. It was indeed the whitelist i had to add.

---

