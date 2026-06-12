---
title: "Disabling of ICMP Service using sysctl is not working"
date: 2019-10-24
forum: General Help
---

### Post by prithvi1 on 2019-10-24
I am running 16.04.6  LTS with kernel 4.15.0-65. I would like to disable ICMP. To achieve this I have added the following lines into  the sysctl.conf file 


net.ipv4.icmp_echo_ignore_all = 1

net.ipv4.icmp_echo_ignore_broadcasts = 1



The  problem is that after a reboot the configuration given above is not  applied. The entries are there in the sysctl.conf file but the ICMP  services are not disabled. What can be the reason behind this? Do I have  to do something extra so that the changes that I have put in the  sysctl.conf are picked up after every restart or after a shutdown-boot?

---

### Post by SeijiSensei on 2019-10-25
You can also use an iptables rule:
```
sudo /sbin/iptables -I INPUT -p icmp -j REJECT
```

I'm surprised that adding those directives to sysctl.conf doesn't persist.  

Another option is to add 
```

echo '1' > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo '1' > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

```
to the file /etc/rc.local which is run at the end of the boot sequence, though I don't see why that should be necessary after changing sysctl.conf.

---

### Post by prithvi1 on 2019-10-27
Yes I am also surprised at this. All of my other Kernel parameters are getting persisted at bootup. Only this parameter is not being persisted. Is there a mechanism where we can have Kernel log into the boot log (, i.e. /var/log/boot.log) or any other logging place what kernel parameters are getting changed? I even checked > journalctl command and was not able to figure out anything. 

Disabling ICMP responses from the firewall is my last option. I wanted to have Kernel itself stop responding to or listening to for ICMP requests.

---

### Post by HermanAB on 2019-10-27
Bear in mind that ICMP is actually a useful protocol and if your network stack works properly, you need not disable ICMP to mitigate nonsense such as ping floods.

---

### Post by prithvi1 on 2019-10-29
It is not only ping floods or sync attacks which I plan to harden the desktop against. I plan to harden it against most of the network attacks. So that was why I was wondering on why is the Kernel not persisting the changes in the parameters? Is there is mechanism which is overridding these parameters and is there somehow I can determine which program/service/daemon is setting kernel parameters apart from sysctl?

---

### Post by HermanAB on 2019-10-30
Well, the Linux network stack is pretty good as is and any further 'hardening' won't make any practical difference at all, but go ahead, it won't do significant harm.

---

