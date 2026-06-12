---
title: "Starting a Home Server Network from Scratch (with VPN also)"
date: 2020-05-17
forum: General Help
---

### Post by eoshibruno on 2020-05-17
Hello to everyone!!!!!!!

I’m new and I want starting from scratch a Virtual Home Server with many functions and that it can be linked to other external servers via secure vpn.

I think to create a Primary Server (with mail service, vpn service, vhost service) connected to a firewall. A Home Server connected to a firewall. A game server (with irc server, bbs server and other) connected to a firewall.
The router go through the firewall and the Main Server to a switch where are linked the other servers and also the secondary Wi-Fi router.
I’d like to give a name to my Server/Home Virtual LAN in order to connect it to my parents home server.
for example if my Provider IP (Public IP) is 2.263.971.270 I’d like to set it on my Primary Server and link it to a Virtual Host......so the IP 2.263.971.270 will be bruno.familyserver.srv in order to set also the IP of my parents to a vhost like parents.familyserver.srv.......and also set a virtual mail server for exchange mails for example with a virtual address as [email]bruno@familyserver.srv[/email] and [email]alberto@familyserver.srv[/email].
it’s possible to do that? Is correct the way I’ve think to connect and protect servers?!?!?
thank You so much for your help!!!!!!!

---

### Post by TheFu on 2020-05-17
Do you intend for these servers to be accessed from the internet?  That puts in all sorts of restrictions that are outside your control.  Running an email server at home is easy. Running an email server that is part of the internet from a residential internet connection is not easy, usually impossible.  Do you own the "familyserver.srv" domain already?  I don't think "srv" is an approved TLD.
familyserver.org, familyserver.net, familyserver.com are already taken.  Perhaps a country-based LTD could work?  familyserver.us.co is taken. familyserver.uk.co seems to be available.  Open the wallet.

Using double-NAT makes lots of things harder.

I'd start by breaking down the problem in to bite sized chunks and opening a thread about each.  

First would be about network architecture. Systems that don't need internet, shouldn't be on the same subnet as those that do.

Second would be about the selection of hypervisor.

Third would be able infrastructure services for authentication, DNS, DHCP, storage.  DNS will be required.

Get a list of different OSes involved too. Do you want VMs or Containers or Chroot/Jails?  Each has pros and cons.  Depending on which you select, the expertise will have to come from different sources. There are 10 different VM solutions. 10 different Containers.  Nobody knows all of them.

Tightening up on terms will be needed too, since "virtual host" means different things.  Could be a VM, a container, or just a different webapp.

No way would I use wifi.  Wifi traffic needs to be treated like raw internet traffic and shouldn't be trusted.  If you have wifi, then you'll need a VPN solution that you host. Should be able to share the same VPN used from the internet if the network architecture is correct and doesn't have double-NAT.

In the old days, I'd send you to "RateMyNetworkDiagram.net" which had thousands of different network diagrams for all levels of networking, so you could see how this stuff works and understand the sort of information that needs to be shared.  You can see a few in my profile here under the photo albums.  May provide some ideas.

---

### Post by eoshibruno on 2020-05-17
Hi.

Yes, server will have access in internet but will be accessible only via Virtual Private Net.
I&#8217;ll use the virtual host for the mail and will have only access internally via VPN. familyserver.srv is created virtually and will be linked to the Public IP give by the Internet provider.
About Wi-Fi........Main Wi-Fi router will be deactivated in order to protect access, and all Wi-Fi connection will be obtained from a second router with Wi-Fi transmitter under firewall.
About the OS......home server and game server will run under Ubuntu Server (dedicated) and guests can only have access to a Wi-Fi router protected.
Thank You so much for your answers.

---

### Post by TheFu on 2020-05-17
Seems you are making all sorts of assumptions that may not be possible.  An internet connected email server will be blocked by almost every other email server in the world unless it is on a static IP with both forward and reverse DNS lookups working.  Sending email out to 1 account that you control isn't hard. Sending emails out to the world will be impossible for most home users.

Please draw a diagram and post it in an album here. Label the subnets clearly.  I'll take a look.

Wifi behind a firewall doesn't help security any. Wifi is the issue unless you live in a cave 2 miles from everyone else. There is no fix for that except using a VPN for any traffic that traverses wifi.  You did say you cared about security.  If you don't, fine. 

Using "virtual" or "virtually" doesn't make the details unimportant. Assume that "virtual" is removed and try to answer the questions.

Please draw a diagram.

---

