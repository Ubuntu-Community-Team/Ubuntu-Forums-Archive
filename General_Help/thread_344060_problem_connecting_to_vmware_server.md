---
title: "problem connecting to vmware server"
date: 2007-01-22
forum: General Help
---

### Post by ac251404 on 2007-01-22
I just did a fresh edgy install on an old PC I had and put a 400gb hd in it to act as a file server. The problem is I would like to run a windows mce virtual machine to stream movies to my xbox. Now I got the virtual machine installed and running okay (havent test xbox connectivity) but then I started playing around with the idea of connecting to the windows vm from my laptop so I could reboot/troubleshoot without having to a hookup a monitor anytime something went wrong. So I installed vmware server on my laptop as well and am trying to connect from the VMware server console.

The VM is setup with bridged networking so it has its own IP address separate from the host OS. The host OS has a login/pass and the windows vm has a different login/pass. So now I have 2 ip addresses, and 2 logins and I'm not sure which I should be using to connect to the VM. Do I use the ip address of the host machine and the login/pass of the host machine? I have tried this and believe it is the correct way but I keep getting 'connection refused'. Do I need to open any ports with iptables (this is a fresh install with no firewall setup)? I have also disabled the windows firewall in case this matters. Does it matter if I am connected to the vm on the server thru localhost while trying to access it from my laptop as well? I have tried many configurations with no luck whatsoever. 

Basically if I could just get some input on the typical way this way should be setup and the procedure to connect remotely it would be much appreciated.

thanks

---

