---
title: "Remote Network  Management Project Help"
date: 2007-10-03
forum: General Help
---

### Post by dpsguard on 2007-10-03
Hi All,

I am looking forward to advice on setting up a low cost implementation of a ubuntu linux based solution, wherein I can monitor 3 point to point radio linkls ( outdoors 2.4/5.8Ghz radio bridge links supporting snmp and they are all in different cities), via a central location (my house). 

I wish to install a small BookPc at master end of each of the point to point link location (master end of each link has internet access whereas far end does not is thus conected to main site in each location via a license free WLAN outdoor gear) and monitor the health of both ends of each radio link.  

The book PC at each city master site can have some open source snmp application that can receive traps / events from the radio equipment and then forward it over to the a central location ( in this case my house) via some VPN. These sites do not belong to the same organization, so there can be overlap of private address space. So each of the remote city bookpc will need to have some VPN client that needs to have a continuous VPN tunnel to my Box at home to be able to send the traps and alerts. 

Over this VPN network, then I should also be able to VNC in any bookPC and then log into corresponding radio devices.


Please advice as to the best way to implement this as I do not have more than $5000 budget in all for this project. For a non profit group of organizations.

I briefly looked at nagios but do not have any experience with it. I will also need to know what kind of linux vpn package will do the job.

Thanks

---

