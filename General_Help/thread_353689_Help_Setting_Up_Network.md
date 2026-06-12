---
title: "Help Setting Up Network"
date: 2007-02-05
forum: General Help
---

### Post by orcalover on 2007-02-05
Finally reaching the point where I have had enough of Window's crap, I recently installed Ubuntu as a replacement of Microsoft's Small Business Server. I am now trying to setup our home office network with Ubuntu so that it works in a similar fashion to the way our windows network operated. 

Here is what I am trying to do:

1) I want to setup my main desktop to act as the network server and domain controller. Each additional computer will act as a workstation. 

2) I would like to setup the network so that users can login to any computer on the network with their username and password. I would also like to make use of "roaming profiles", where each users files (ie, My Documents, internet favorites, etc) are stored on the network server, thus enabling them to login to any computer and have access to all their files and settings. 

3) I will also be hosting an internet-accesible website with it's own domain name that will be used to host email, in addition to serving both our intranet and internet site. 

With the Windows server setup, we had to setup a local domain name (domain.local) and an actual internet domain (domain.com). Since we have a cable connection without a static IP address, I use DynDns.org to handle the internet domain. 

The hardware setup is as follows:

Modem: Cable
Router: Linksys WRT54GP2

The server has two nic cards, one goes directly to the router and the other goes to a switch which provides the connection to all other computers on the local area network. 

At this time, I've setup Ubuntu Desktop on the computer I want to use as the server, and installed and configured ddclient (for dyndns.org). I've also installed, but have not configured, firestarter (firewall) and samba (network - for windows?). 

Currently, the linksys router is setup to act as a local DHCP server, but I'm not sure if I should disable this or not. 

I've looked at the documentation, as well as searched the forums and google for additional information. I also purchased the book Ubuntu Unleashed, which I am also referencing. However, I'm not sure I fully grasp what I need to do to setup things up. 

Can anyone help me out here, or point me to a tutorial that can walk me through some of the basic steps. Mainly I need to figure out how to setup the server, and how to setup the workstations to get information from the server. 

I'm also somewhat confused regarding setting up user accounts. Will users that have been setup on the server using the System > Administration > Users & Groups be setup as network users, allowing them to login from any computer, or is there another method to adding users to the network.

Some of the things I have read seem almost too simple. Coming from a windows setup where everything is complicated beyond compare is making this a bit hard for me to grasp. I'm still in awe over how simple the installation of Ubuntu is (less than 20mins to setup?). I nearly passed out when everything worked after installing Ubuntu - didn't have to load any drivers, the internet just worked, it's literally shocking). 

Nonetheless, I seem lost in the simplicity of all this, so any help would be appreciated. 

Thanks in advance, 

Sean

---

### Post by MoLE on 2007-02-11
First suggestion I'd like to make is - if you're going to have your desktop as a mission-critical server in your network, then ensure that you've chosen a stable release, such as Dapper - 6.06 LTS as it will be supported for at least 2.5 more years.

In terms of what you need to do to set up ubuntu as a samba domain controller - have a look at the [howto forge ]("http://www.howtoforge.com/samba_setup_ubuntu_5.10")article on the subject.

You will need to get down-and-dirty with the commandline to set everything up correctly.  At the moment, there are few nice GUIs for server functions under linux.

---

