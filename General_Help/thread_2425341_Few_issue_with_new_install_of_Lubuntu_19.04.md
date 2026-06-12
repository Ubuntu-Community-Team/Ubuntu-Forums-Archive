---
title: "Few issue with new install of Lubuntu 19.04"
date: 2019-08-24
forum: General Help
---

### Post by fozziebear on 2019-08-24
I have previously been using Xubuntu 17.04 on an old HP Pavillion Core Duo based system with 2gb Ram. The latter cannot be upgraded more than 2gb so I have been looking at other options hence Lubuntu. I also had instances of Xubuntu freezing which I put down to memory leak from Chromium by leaving the tabs open all the time (I've had similar memory leak on Windows 10 pcs with Chrome) so thought the lower memory requirement of Lubuntu would be more suitable.

My main (only) requirements were to install ***get_iplayer ***from Jon Hedgerows PPA and also ***Deluge***. Also I needed to browse my windows network which is now primarily Windows 10 machines which have SMB v1 disabled and 17.04 does not support SMBv3. 

I tried Lubuntu from a live USB support and was surprised how quick network browsing was using the built in PCManFM-Qt File manager and I easily connected to existing windows network shares. I also was able to easily install the get_iplayer PPA.
 However now I have installed Lubuntu to the hard drive I cannot browse the network at all. If I click on Windows network it is completely blank. Also whilst I can download and install Deluge it will not work complaining of Blocked Ports. Previously I have never had to open ports on my router as I assume UPnP worked out of the box.
I appreciate Lubuntu is a very light distro but are things like UPnP missing by default and what has changed as regards networking from a Live install to a full install.
Any guidance would be appreciated.

---

### Post by SeijiSensei on 2019-08-24
Try using Transmission.

---

### Post by fozziebear on 2019-08-24
> **SeijiSensei said:**
> Try using Transmission.

Thanks, I have tried transmission but the same results -it claims ports are blocked. I also prefer the interface of Deluge to Transmission.  As I said I never had this with Deluge on Xubuntu.
I wondered if the same networking issue was preventing me from browsing the windows network??

---

### Post by fozziebear on 2019-08-25
Just a thought. Is Samba installed by default in Lubuntu 19.04? If not  what does the file manager use to browse the network on a live image?

---

### Post by coffeecat on 2019-08-25
The Ubuntu/Debian based sub-forum is for:

> Support for Ubuntu or Debian based distributions - not for Official Ubuntu flavours

Lubuntu is a well-established official flavour of Ubuntu.

*Thread moved to **General Help**.*

---

### Post by SeijiSensei on 2019-08-25
Are you running any sort of firewall on the Lubuntu machine?  If so, turn it off, and try again.

---

### Post by fozziebear on 2019-08-27
> **coffeecat said:**
> The Ubuntu/Debian based sub-forum is for:



Lubuntu is a well-established official flavour of Ubuntu.

*Thread moved to **General Help**.*
Apologies I am still new to Linux and its variables and didn't know which sub forum to post :-)

---

### Post by fozziebear on 2019-08-27
> **SeijiSensei said:**
> Are you running any sort of firewall on the Lubuntu machine?  If so, turn it off, and try again.
No No firewall. I have resolved the networking issue by installing Samba and all is now fine browsing the local Lan. It also appears to have resolved Deluge. I have closed the previously opened port in my router and set the port back to random in Deluge and torrents now download. UPnP must rely on a component of Samba or its dependencies?
Thanks for your help.

---

