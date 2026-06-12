---
title: "How to stop my system from using random MAC?"
date: 2007-08-16
forum: General Help
---

### Post by your_peak on 2007-08-16
I have "Ubuntu 7.04 - the Feisty Fawn" installed on my HP pavilion v7060(jp) PC, which
is located in my university.

You see, my PC use DHCP way to get the IP&#12288;address. But sometime, the system use
random MAC to get IP address, which is a potential problem in the network if
it requires too many IP&#12288;addresses by changing its MAC. So I want to disable the
function that changes MAC address automatically.


When such thing happens,there will be a system log in system.log and kernel.log
like this:

> 

/var/log/kern.log:Aug 10 14:06:35 xfliu-desktop kernel: [  866.860000] Please complain to your hardware vendor. Switching to a random MAC.



I googled on internet and was told that sth wrong with "forecedeth", but I have
no idea to deal with.

So could anyone give me any advice or help?


P.S. 

Such problem does not happen too often. It seems it occurs when the system
failed to wake up from sleep mode, when the system seems to freeze and 
there is only mouse on the screen.

---

### Post by your_peak on 2007-08-20
I have stopped it but in a quite complex way, which is not recommended for you.

I overwrote the driver of net card and forced the MAC address to be the right one.
Then no random MAC will appear.

The detailed thing can be found here but in Chinese.

[URL="http://xfliu.blogspot.com/2007/08/linux.html"]
http://xfliu.blogspot.com/2007/08/linux.html[/URL]

---

### Post by wirelessmonkey on 2007-08-20
This is a rather serious problem with your network card, and if you were connecting on my network, you would recieve a special visit.  I highly suggest you do 2 things. 1) Contact HP and get your NIC repaired or replaced/ get a different network card.  2) Create a script to set your MAC to the same address at start.  Reply if you want help doing that.
I say this only because you are on a University Network, and this can cause serious problems if your NIC spams multiple bad MAC addresses, which would be fairly easy to track and probably would be a violation of your campus IT policy.

---

