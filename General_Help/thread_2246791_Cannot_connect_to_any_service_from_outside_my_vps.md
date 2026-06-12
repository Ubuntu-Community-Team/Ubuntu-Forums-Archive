---
title: "Cannot connect to any service from outside my vps"
date: 2014-10-03
forum: General Help
---

### Post by computergroove on 2014-10-03
I just purchased a .99 vps from atlantic.net. It comes with 256 mb ram, 10gb hard drive and 1 TB data per month. I installed Ubuntu 14.04 server and I proceeded to install squid3 as per the server guide -> [https://help.ubuntu.com/12.04/serverguide/serverguide.pdf](https://help.ubuntu.com/12.04/serverguide/serverguide.pdf). All went exactly as explained. I can ping the server from my local computer and the ufw firewall is not installed and there is no firewall or NAT on the server side. When I tried the public IP address with my custom port in internet explorer I get no internet traffic at all. When I remove the proxy settings the internet works again - proxy isn't working right? So I re provisioned (reinstalled) the installation of Ubuntu Server and tried to install telnetd just to see if I could connect to something and it failed. I then tried to install sshd and it failed as well. I can ping the server and its a new install (4-5 times now) and I am stuck. I cannot get anything to connect to the remote host. I have:

1. Successfully pinged [www.google.com](www.google.com) from the server
2. Succeddfully pinged the server ip from my local computer
3. Reinstalled and tried Ubuntu Server 12 x32, 14 x32 and 14 x64 and configured telenetd sshd and squid3 with multiple configurations which I got from the official manual and, when they didn't work, several different user posts on the net which also failed. 
4. I spoke to tech support at atlantic.net and they confirmed that there is no hardware or software firewall or NAT that needs to be port forwarded or disabled. 

I am stuck. Any help would be appreciated. What I want to do is use the box for a proxy server - that's it.

---

### Post by computergroove on 2014-10-03
I got it. For some reason my ifconfig was telling me that my local ip began with 69.29 and when I did a:

ip addr show eth0|grep inet|awk '{print $2}' | sed 's#/.*##'

from the terminal it returned 69.28 as the ip address.

---

