---
title: "vmware server - guests to separate vlans"
date: 2008-03-05
forum: General Help
---

### Post by Sgurd on 2008-03-05
I have an Ubuntu host with multiple VMs in VMWare Server using bridged networking.
The host is on our "LAN" VLAN (subnet?) so all guests are on the "LAN" VLAN.
Now, I'd like to have, say, one guest in the "LAN" and one guest in the "DMZ".
Is this doable?  

I could do multiple NICs if needed.  
Our switches are HP ProCurves . . .

   Thanks - JD

---

### Post by Joe Mama on 2008-07-16
Yes you can - :) 

In fact I am doing something similar to this now. (I am going to cut and paste what I have found on this elsewhere)

I have 2 different subnets that have different needs and yes I had to keep them seperated. My 10.x.x.x network is our "Normal" domainified network that everyone gets a chance to play on and can see the outside. This is eth0. 


My other is 192.168.x.x this card is eth1 and its own little virtual world separated from the network (sort of host only) This allows me access to the server from either connection depending on which vlan I am on. I hope this answers your question or gets you closer to a solution. :)

-snip-
Using VMware Server 1.0.x:

1) Install the network card in the host PC
2) Ensure that the network card works in your Ubuntu installation. ie: It should show up as "eth1", assuming your first network card is "eth0".
3) As root, run "vmware-config.pl". Warning This will stop your Virtual Machines if they are running.
4) Follow the prompts until it asks you about Networking. In the section below, I am adding a second bridged interface on the vmnet2 network:
Code:

You have already setup networking. 

Would you like to skip networking setup and keep your old settings as they are? (yes/no) [no] no 

Do you want networking for your virtual machines? (yes/no/help) [yes] yes 

Would you prefer to modify your existing networking configuration using the wizard or the editor? (wizard/editor/help) [wizard] editor 

The following virtual networks have been defined: 
. vmnet0 is bridged to eth0 
. vmnet1 is a host-only network on private subnet 172.16.1.0. 
. vmnet8 is a NAT network on private subnet 172.16.117.0. 

Do you wish to make any changes to the current virtual networks settings? (yes/no) [no] yes 

Which virtual network do you wish to configure? (0-99) 2 

What type of virtual network do you wish to set vmnet2? (bridged,hostonly,nat,none) [none] bridged 

Configuring a bridged network for vmnet2. 

The following virtual networks have been defined:
 
. vmnet0 is bridged to eth0 
. vmnet1 is a host-only network on private subnet 172.16.1.0. 
. vmnet2 is bridged to eth1 
. vmnet8 is a NAT network on private subnet 172.16.117.0. 

Do you wish to make additional changes to the current virtual networks settings? (yes/no) [yes] no

5) Answer the rest of the questions to finish setting up VMware.
6) You can now add a second virtual Ethernet card to the VM via VMware Server Console, and bind that Virtual Ethernet adapter to a "Custom" network, specifying the network you added (vmnet2 in the example above).

Hope that helps. I haven't played around enough with the VMware Server 2.0 Beta to tell you how it works in the new version.
-snip-

---

### Post by mustimasti on 2008-07-18
hi, even i m doing same kind of network but i like to tell u more and i need yr help

I have installed ubuntu server and i have 2 lan card as below

eth0(Lan)
10.0.0.2
255.255.255.0
Gateway - 192.168.16.23(Wan ip address)

eth1(Wan) from where i am getting internet
192.168.16.23
255.255.255.0
192.168.16.2

now i have installed vmware server and in that again i have installed ubuntu server and i have to do  following things

eth1(WAN) to NAT
eth0 to bridge

basically i am making vmserver as my main server by configure ldap, dns, dhcp proxy on eth0 and then it will go to switch and then all the client computer will join the domain, need your help

do i do the same way you have done if u can give me as example then it will be easy for me to understand and implement

my email addess is [email]mustafa.chittalwala@gmail.com[/email]

---

