---
title: "Jammy Jellyfish network problems"
date: 2022-05-10
forum: General Help
---

### Post by meldalinn on 2022-05-10
Hi there. The update to jammy jellyfish was a bit problematic for me. 3 out of 15 ubuntu servers got networkproblems afterwards.
They got the network adapter reset to disabled and the configuration deleted.
I got them all manually configured, back online and installed netplan to manage the network configuration. The problem ive got now is that i cant get the DNS settings to persist over a reboot.

Netplan config:
```
network:
  version: 2
  renderer: networkd
  ethernets:
    ens160:
      dhcp4: true
      nameservers:
        addresses: [192.168.2.128, 192.168.2.129]



```

I dont know if netplan needs the resolv.conf file to set the DNS?
Anyways, it does not. The resolv.conf is blank until i run ```
dhclient -r; dhclient
``` After which the resolv.conf is created with the correct configuration, and i can verify that the correct DNS server is being queueried.

---

### Post by TheFu on 2022-05-10
If you enable DHCP, then the DNS settings should be provided by the DHCP server. Remove the last 2 lines.

And you might want to add a 
```
   dhcp6: false
```
line.
Then run 
```
sudo netplan generate
sudo netplan apply --debug
```

to force the changes to be seen.

---

### Post by meldalinn on 2022-05-12
Thank you so much. It works now. Amazing community.

---

