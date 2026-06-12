---
title: "No network connection (anymore) when running Ubuntu 14.04 LTS with VMWare Player"
date: 2016-05-09
forum: General Help
---

### Post by Chris_Laskaris on 2016-05-09
I am running Ubuntu 14.04 LTS on a virtual machine with VMWare Player. Until recently, I was able to connect to the internet using the shared IP address of the host computer (i.e. I am using the NAT option for the network adapter in VMWare Player). Now, suddently, it does not work anymore. When I load Ubuntu 14.04 LTS, I get the message: "Disconnected - you are now offline". System Settings > Network shows an "unmanaged" wire network with only a machine address, no IP or anything else is displayed. When I click Options, I get the message: "Error editing connection: Did not find a connection with UUID '(null)'".

I am able to connect to the internet on another virtual machine on VMWare Player, which runs Ubuntu 12.10. So I suspect the problem is "inside" my Ubuntu 14.04 LTS rather than with VMWare Player.

I did extensive searching on the web on how to try and get the network back, but none of the proposed solutions I have found so far has worked for me. I'd be grateful for any help regarding where I should start and what I should check.

---

### Post by steeldriver on 2016-05-09
If network manager is showing the connection as unmanaged, then presumably you configured it via the /etc/network/interfaces file? if so, what are the contents of that file?

---

### Post by Chris_Laskaris on 2016-05-09
The content of the /etc/network/interfaces file is:

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

---

