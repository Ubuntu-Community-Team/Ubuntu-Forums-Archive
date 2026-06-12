---
title: "[SOLVED] DHCP release IP"
date: 2007-12-12
forum: General Help
---

### Post by cotcot on 2007-12-12
1.  I am searching for a command to release my IP lease from the cable provider in order to get an IP when I boot another distro on the same hard disk within the lease time of 2 hours.
DHCP3 is installed.
I tried ```
sudo dhclient -r eth0
``` without succes.

I tried ```
sudo ifdown eth0
``` without succes.

I know that the command ```
sudo dhcpcd -k eth0
``` works when "dhcp" installed instead of "dhcp3".

The command with the same result in windows is ```
ipconfig /release
```

2.   I am also looking where I should park this command to have it executed automatically at shut down of the pc.

Thanks

---

### Post by lsutiger on 2007-12-12
If you restart networking it will release and renew your IP. 
sudo /etc/init.d/networking restart

---

### Post by cotcot on 2007-12-13
It did not work either for the distro that I am testing (elive) although normal reboot from my gutsy to my feisty install is working fine. I saw that the netconnection the test distro is even not working anymore after the lease time of 2 hours is elapsed. So it seems to be a bug in the test distro. (it was working during install and a couple of days after the install).

---

