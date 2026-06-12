---
title: "Cloudmin says DHCP server is not running while creating KVM VM, even though it is"
date: 2017-07-11
forum: General Help
---

### Post by david396 on 2017-07-11
[COLOR=#444444][FONT=&amp]Hello,[/FONT][/COLOR]
[COLOR=#444444][FONT=&amp]I am new to Cloudmin/Virtualmin ,I am trying to create a KVM VM using Cloudmin and Webmin running on Ubuntu 16.04 lts. I am using the GPL version. This is being used on my local home network. I have installed DHCP server in the Webmin modules and added the subnet I assigned in Cloudmin which is 192.168.2.x. I added the subnet to the DHCP server with these settings: Network address: 192.168.2.0 Address Ranges: 192.168.2.1-192.168.2.255 Netmask: 255.255.255.0. I have not done anything else on the DHCP settings other than save and start. When I try and create a new KVM system, everything goes fine except that it says "Adding DHCP entries .. .. DHCP server cannot be configured : The DHCP server on your Cloudmin master system is not running"[/FONT][/COLOR]
[COLOR=#444444][FONT=&amp]I have followed Multiple guides in the Virtualmin Documentation but I am still having this issue. My normal home network is running on the 192.168.1.x subnet as well. I am also seeing that DHCP server is running in the system bootup shutdown tasks in webmin, I have also set dhcp to boot on startup.
[/FONT][/COLOR]
[COLOR=#444444][FONT=&amp]I also added a bridged network device following this guide: [https://www.virtualmin.com/documentation/cloudmin/virtualization/kvm](https://www.virtualmin.com/documentation/cloudmin/virtualization/kvm)
[/FONT][/COLOR]
[COLOR=#444444][FONT=&amp]This is the one I followed for the DHCP server: [https://www.virtualmin.com/documentation/cloudmin/ifaces](https://www.virtualmin.com/documentation/cloudmin/ifaces)
[/FONT][/COLOR]
[COLOR=#444444][FONT=&amp]As well as this one [https://www.virtualmin.com/documentation/cloudmin/virtualization/empty](https://www.virtualmin.com/documentation/cloudmin/virtualization/empty)

I am not sure what else to try and what other information I need to provide, let me know and thank you!

(I have also posted this on the forums at cloudmin but no one has said anything [https://www.virtualmin.com/node/52778](https://www.virtualmin.com/node/52778))


[/FONT][/COLOR]

---

