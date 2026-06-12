---
title: "PennState Wireless"
date: 2007-03-27
forum: General Help
---

### Post by ZERO_SHIFT on 2007-03-27
I am having problems connecting to PennState's VPN wireless network eventhough I installed their linux vpn client. I installed CISCO based vpn clients through synaptic but with no luck.Any ideas?

Thanks in Advance
__________________

---

### Post by cburwell on 2007-04-11
I have been having some problems with the wireless at the delco campus lately. I can connect to the network, and I can connect to the VPN fine. However, once I am connected to the VPN I cannot get anywhere! I am convinced that it is a problem with the Cisco VPN software on my computer (I am not running Ubuntu anymore, but rather Kubuntu).

Anyway, I would suggest that you download and compile the VPN client from this URL:

[https://downloads.its.psu.edu/](https://downloads.its.psu.edu/)

This will not only install the VPN client, but it will also install the connection profiles for the PSU campuses. So, all you will have to do is issue the command "sudo vpnclient connect delaware". You will substitute delaware for the name of the profile of main campus.

---

### Post by ZERO_SHIFT on 2007-04-12
Hi,

I got mine working last week. I contacted the guy who made the Linux VPN client here in University Park, and guess what linux distribution he was running on his laptop?!:D 

He gave me the following command:
```
su - root
pkill dhclient
 /etc/init.d/vpnclient_init start
 iwconfig eth1 mode Managed
 iwconfig eht1 essid pennstate
 dhclient eth1
 vpnclient connect university_park

```

I beleive that you should put your campus name in the last line.
I created a bash script for the command to make it easier. As for shutting the VPN client down its:
```
 /etc/init.d/vpnclient_init stop
```

Let me know if it works.

---

