---
title: "Internet Problems"
date: 2006-11-25
forum: General Help
---

### Post by ChrisNTR on 2006-11-25
I don't think this is a Ubuntu specific problem, more Linux but I'm having problems connecting to the internet from my laptop at uni.

There is only one connection in the room and it is limited by MAC address. I'm currently on the connection at the moment on my apple machine. If I try and connect using DHCP only on the apple machine, it doesn't connect, if I use DHCP with Manual [IP] address.. then it'll connect. 

I was wondering if there was a way of doing something similar on Ubuntu. 
I've tried going sudo ifconfig eth0 $IPaddress up
and sudo /etc/init.d/networking restart but neither work. 

Any help would be appreciated. 
ChrisNTR

---

### Post by wastrel on 2006-11-25
Configure your card in /etc/network/interfaces   

Open /etc/network/interfaces in your favorite text editor (needs sudo) and add a block like this for your eth0 card:

```
iface eth0 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1
```

Adjust the IP addresses and netmask to your local situation.  

After that just ```
sudo ifconfig eth0 up
```

To make it automatically come up when you boot, add a line ```
auto eth0
``` at the bottom of the /etc/network/interfaces file.

---

### Post by ChrisNTR on 2006-11-25
Okay, I've tried that and all that does is give me the IP address
169.254.121.49 Which is just a random address which doesn't work. (Under nm-applet).
However ifconfig says that eth0 is configured correctly.

When I run dhclient before, I get DHCPOFFER from 130.88.191.250 abd then it used to bind me to my assigned IP address but now it just repeats DHCP request on 255.255.255.255 and DHCPNAK and DHCPOFFERs.

I would normally go, fair enough, it doesn't work but I've got it all working on the mac pretty easily so it should work, cheers for the help.

ChrisNTR

---

### Post by calx on 2006-11-25
Are you running Ubuntu on your apple? Because if it's another machine, as you indicated your connection is limited to a specific MAC address, it's not gonna work on anything else but the apple.

---

### Post by ChrisNTR on 2006-11-25
I've spoofed the MAC address on my laptop (sony laptop) so that it works with the connection. I've been using my laptop fine on the connection for the past month or so. Yesterday I went to my friends and was using her internet whilst spoofing her mac address. I managed to connect on my ip address with her mac address but I quickly disconnected. After that it hasn't worked on my laptop but works fine on the apple machine.

---

### Post by wastrel on 2006-11-25
I don't use nm-applet , so can't comment on it.  Try disabling it and see what happens -- it may be trying to reconfigure the interface automatically and causing problems.

My understanding was that you wanted to manually configure the eth0 interface, not use DHCP, and that's what my instructions were for.  If this is the case then you shouldn't be using dhclient.

After adding the eth0 block to /etc/network/interfaces, what happens when you try to bring up eth0 with ifconfig?  

After this can you ping the gateway?  Can you ping the internet?

I feel like I'm missing something here... :]

---

### Post by ChrisNTR on 2006-11-26
Right, I can broadcast ping the gateway when I'm "connected" to the network however I get "Unknown host" when I try and ping the internet. This is when I explicitly define the ip address/broadcast/netmask in the ifconfig line. If I just use ifconfig eth0 up it won't show the inet addr or Bcast etc in ifconfig.

Cheers again for your help.

---

### Post by ChrisNTR on 2006-11-27
I can connect on the internet whilst elsewhere so it's not a global problem.

---

### Post by wastrel on 2006-11-27
Ah, you're not using DHCP so you need DNS servers naturally :]  I should have thought of that. 

Figure out what the DHCP server is handing out for nameserver addresses and stick them in /etc/resolv.conf
```

nameserver 111.111.111.111
nameserver 222.222.222.222
```

---

