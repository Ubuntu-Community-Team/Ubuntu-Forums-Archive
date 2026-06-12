---
title: "VPNC connects but doesn't redirect traffic"
date: 2007-03-05
forum: General Help
---

### Post by FIONEX on 2007-03-05
Hey

I connect to my university's network using the VPNC plugin for networkmanager.  The thing is, after the connection is established, the traffic is still directed through the main wireless IP address to the university.  However, it should be going through the tunnel IP created by the VPN.  I know this because when I type "route -n", only the main ip is in the routing table.  How do I reroute all traffic through the VPN tunnel IP?

Thanks

---

### Post by FIONEX on 2007-03-05
Any idea on how I could route all traffic through a certain device or IP address?

---

### Post by linuksamiko on 2007-04-17
Same problem here. It used to work under edgy but stoped working under feisty. I gues it is a networkmanager problem

---

### Post by CyborgMax on 2007-05-02
I have the same Problem. (in feisty. But i did not tryed it in edgy.) But i don't think it is a problem of the network-manager-vpnc. Try to execute vpnc in terminal - you will get the same results: connection success but no traffic. 

I compiled Cisco VPN Client. It is working but i don't like it. Hope there will be a fix in the next time.

---

### Post by balak on 2007-05-03
Hi,

I am also having issues with vpnc since yesterday. The funny thing is that I haven't changed/added/modified anything in my system that could have affected this. [I added libxaw6 and libmotif3 for Citrix Client]. I have always used the command line version of vpnc [network-manager never worked for me]. Now, everytime I am able to login successfully but no connection is established.

I use linux exclusively @ home and if this breaks I can't connect to work anymore :(

---

### Post by codedmin on 2007-05-03
Hy there, i'm have problems too. 
My traffic is redirect, but my connection go down after some 5 seconds, 1 minute, is very unstabble.

Any info??
Thanks

---

### Post by codedmin on 2007-05-03
Can fix the problem
> 

I've solved it by rebuilding without the patch:

cd /usr/src
sudo apt-get source vpnc
cd vpnc-0.4.0/debian/patches

sudo gedit 00list

remove the line 06_stolen_from_head

cd ../..
sudo debian/rules binary

cd ..

sudo apt-get remove vpnc
sudo dpkg -i vpnc_0.4.0-2ubuntu1_i386.deb

if you had installed network-manager-vpnc you'll have to reinstall it

be careful when upgrading the system, don't update vpnc or you will get the patched version


Solution from artt  in [https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/93413](https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/93413) comment [26]("https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/93413/comments/26")

Hope could help you

---

