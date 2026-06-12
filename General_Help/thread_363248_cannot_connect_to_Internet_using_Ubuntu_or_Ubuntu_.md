---
title: "cannot connect to Internet using Ubuntu or Ubuntu LiveCD"
date: 2007-02-16
forum: General Help
---

### Post by billdotson on 2007-02-16
I started up Ubuntu and I couldn't get any internet.  I then tried the LiveCD.  No luck.  I then started up Windows and had internet.  After awhile though the internet went down and I couldn't use it anywhere in the house.  I unplugged the router and replugged it and then I tried the internet on the upstairs computer.  

The internet was working again, but then I started Ubuntu on this one and there is still no internet.  Then I started Windows and started typing this post.

I have been using Ubuntu for about a week and it has been working fine, but now this.

---

### Post by davidvasta on 2007-02-16
Sound like you either have router issues or something is wrong with the internet connection. Use the command IFCONFIG to make sure you are grabbing a TCPIP address from the router and then make sure you can ping the router for a good while and then see if you can ping google.com or something like that.

You may want to call the ISP while you tinker too so that they can look at it from their end.

-David

---

### Post by JAPrufrock on 2007-02-16
I'm just guessing, but if you have two computers and tried to set up a SSH network, you may have changed your network connection settings to a static IP address. If so, go to system-administration-networking and change the settings to DHCP.

---

