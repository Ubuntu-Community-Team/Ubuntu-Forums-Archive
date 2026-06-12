---
title: "Desperate! VMware/VBox/KVM networking &quot;not working&quot;"
date: 2007-09-16
forum: General Help
---

### Post by finite9 on 2007-09-16
please help me!!  I am getting desperate!

I run Ubuntu 7.04 amd64 on an HP pavilion dv9297ea.  All updates applied.

I used to have an Acer Aspire 5021 with Dapper Drake and I ran VMware 1.01 and 1.02 with bridged networking to be able to connect to my employers VPN.  I could ping the DNS address or IP just fine.

Since I got the HP, I have been testing KVM, and I initially got it all working with a Windows XP sp2 guest and Nortel Contivity client and i could connect to work just fine.  This was probably around Herd 5 or beta release.  Since that time I have not tested connecting to work as I had already verified that it worked, but I noticed that KVM was slower than VMware had previously been with Dapper Drake.

************
Please note that if I run WinXP normally, ie not virtual, then I can ping the vpn host of my employer and Nortel client works fine.  I can also ping vpn hostname from Ubuntu.  It is just when running NAT mode in virtual guest, or when using bridged mode, that I cannot ping external IP's/DNS names, and Nortel client does not work.  So my router is doing VPN passthrough, and DNS resolution is working.  Using NAT mode in all virtual guests, I can access internet, but I cannot access internet in bridged mode in any of the products.
************


Now, I have a desperate need to work from home, and I start KVM, and it will not connect with the Nortel client.  Further inspection shows that it cannot ping the IP either.  In fact, I cannot ping any IP address.  I assume that something is wrong with KVMs networking and im not that savvy about it so I try VMware again.  Same thing here!!  I cannot ping any IP and Nortel client does not work.

Now I realise that maybe bridged networking is maybe faulty?  The NIC is no longer getting an IP from my router, but it is getting a DHCP address from *somewhere* (maybe the Vmware/KVM software is acting as a DHCP server?)  And I am getting a 169.254.x.x address instead of 192.168.1.x from the router.

I try out VirtualBox just for kicks, and this has same issue (after following wiki on how to get bridged networking to work).

I do not seem to be able to use NAT because Nortel client seems in some way determined to be able to connect to the IP.

**********************************************

Big question is:  Why did this work in Herd 5 KVM and has now stopped working with bridged networking?

**********************************************

I *did* buy a new router.  I had a Linksys WRT54GX v2.0 802.11g and I bought a Linksys draft-n router instead cause I fried my other one.    Could this really be the reason that my virtual guests are not getting an IP from the router so the virtual software gives the guest an IP instead?

Whether I am using NAT or bridged in the VMware or VBox guests, I cannot ping the host from the guest and I cannot ping the guest from the host.  I cannot ping the outside world from the guest in either mode, but obviously, with NAT you're not meant to be able to do this anyway.  Using NAT, I get a 10.0.2.x address.

*******************************************************
Big question 2:  How do i get KVM or VMware (or even VBox) to get an IP from my router??  Can I force it?  Note that the WinXP guest is set to auto dhcp at the moment, and setting the IP manually to 192.168.1.x does not work!

I most want to get networking working with VMware or VBox or KVM in that order of preference, as VMware is fast and easiest to setup in bridged mode, VBox is fast, but a bit of a hassle in bridge mode, and KVM is too slow for my needs, but further development may make this a viable option.
*******************************************************

As far as I remember, I did not do any special setup when I installed KVM and created a guest withe qemu.  How to I check/verify/set network mode using KVM?

---

### Post by finite9 on 2007-09-21
bump!

---

### Post by Noahod on 2007-09-26
> **finite9 said:**
> 

I *did* buy a new router.  I had a Linksys WRT54GX v2.0 802.11g and I bought a Linksys draft-n router instead cause I fried my other one.    Could this really be the reason that my virtual guests are not getting an IP from the router so the virtual software gives the guest an IP instead?



I'm having the same problem myself, and I'm just thinking aloud right now.. I know that the WPA standard included some form of authentication while WEP did not... With WEP if you knew the WEP key you were pretty much on the network, while WPA negotiates a whole bunch of security before it allows you to connect... Now this security would be based upon your mac address (maybe??) which would be different if you had a vmware mac address (bridged).. 

Now I've tried wireshark in XP vm guest, and I'm seeing packets, but the packets I send never seem to make it to the network - That is I never get replies. 

I'm sort of wondering if bridging isn't possible with an AP that respects WPA properly, because the AP might be dropping packets if they come from the wrong mac address, even if they have the correct key.. 

Anyway just thinking aloud, if you're able to try it on wep or no encryption or you speak to someone more knowledgeable, let me know.

---

### Post by armware on 2007-10-26
i had the same issue in vbox.
wireless connection or not doesn't matter to your virtual machine - it emulates a wired connection, which it connects to whatever your main os has (in this case wireless).
anyways, the solution was to set dns servers in the virtual machine os. worked instantly.

---

### Post by finite9 on 2007-10-26
ive been using wpa exclusively for the last few years and it all worked in dapper drake.  I think its weird that it worked in kvm with herd 5 of feisty.

I will try the dns tip, but im not that hopeful.

---

### Post by Noahod on 2007-11-04
Still having this problem in gutsy :(

---

