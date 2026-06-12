---
title: "Vmware server - lost network connectivity - vmnet0 broken"
date: 2007-09-25
forum: General Help
---

### Post by Wutzl on 2007-09-25
Hi,

I have been happily running a windows xp guest under vmware server/feisty for quite a while. Now suddenly I no longer have network connectivity under the guest os - I have no idea what happened (I tried opening the vm under a vista host system - but how would this mess up my vmnet on my linux host?)!

I use a bridged connection for internet connectivity and a private connection for folder sharing with the host. The private connection still works.

The bridged connection vmnet0 still receives a valid ip from my wireless router (10.10.10.x), but it ends up receiving an invalid dns sever (192.168.0.1 - when 10.10.10.1, the router, would be correct). Even assigning a fixed IP and a correct dns server does not fix the problem - the guest can ping the gateway, can resolve the domain name, but can't ping the resolved address on the internet.

I also noticed that when ifconfig does not list vmnet0 (even though this is AFAIK the bridged network for vmware).

All other machines connecting to the router receive correct dns servers and can access the internet just fine - so it must be that vmware is somehow messing up the dns server and connectivity on vmnet0 and 1. Anyone has any idea how to fix this? Is there some setting in /etc/vmware to deal with this problem? I already ran vmware-netware-config.pl and set up my bridged connection again and created a second bridged connection - but neither work.

I appreciate your ideas!

Thanks!

---

### Post by veloce on 2007-09-26
Sound like vmware is running its dhcp server and has the wrong settings for dns and gateway.

You could manually set the gateway as well as the ip and dns.

From my notes:

> To disable the automatic dhcp server you need to follow the instructions:
Linux for Workstation 5.x and VMware Server 1.x
1.Open the file /usr/lib/vmware/net-services.sh in a text editor. Update: file is now: /usr/lib/vmware-server/net-services.sh 
2.Locate the following section (lines 697-699, as seen in Workstation 5.5.1, build 19175):
vmware_bg_exec 'Host-only networking on /dev/vmnet'"$vHubNr" \
  vmware_start_hostonly "$vHubNr" 'vmnet'"$vHubNr" \
  "$hostaddr" "$netmask" 'yes'
3.Change yes to no. The resulting section should look like this:
vmware_bg_exec 'Host-only networking on /dev/vmnet'"$vHubNr" \
  vmware_start_hostonly "$vHubNr" 'vmnet'"$vHubNr" \
  "$hostaddr" "$netmask" 'no'
4.Save the file.
5.Run sudo /usr/lib/vmware/net-services.sh restart to restart the service. Update: sudo /usr/lib/vmware-server/net-services.sh restart 
from: [http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=2012&sliceId=SAL_Public&dialogID=8721758&stateId=0%200%208715970&doctag=Author,%20KB%20Article](http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=2012&sliceId=SAL_Public&dialogID=8721758&stateId=0%200%208715970&doctag=Author,%20KB%20Article)



---

