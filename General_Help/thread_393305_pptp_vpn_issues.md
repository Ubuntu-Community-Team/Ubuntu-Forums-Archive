---
title: "pptp vpn issues"
date: 2007-03-25
forum: General Help
---

### Post by g00s3m4n on 2007-03-25
hi all..

after a long time of playing around with linux i have finally taken the plunge to convert my work laptop from windows.

I have installed ubuntu 6.10 and everything is going great.. my only problem at the moment is that I am not able to connect to any of my vpns (unfortunately most are MS PPTP ones)

I have installed pptp-linux and pptpconfig based on the howto i found here:
[http://ubuntuforums.org/showthread.php?t=91249](http://ubuntuforums.org/showthread.php?t=91249)

when i connect, i get the following error:

Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/1
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
pptpconfig: pppd process terminated by signal 16 (failed)
pptpconfig: SIGUSR1

If i try the same VPN connection from my XP box, it works fine..  does anyone have any advice? unfortunately I am not able to complete my day to day tasks without this functionality.

thanks for your help

g

---

### Post by jcbwalsh on 2007-03-25
I had a very similar situation. You might try network-manager-gnome. It has built in support for PPTP VPN. 

James

---

### Post by g00s3m4n on 2007-03-25
thanks for the reply..

forgive my stupidity, but, i have installed it ok, how/where would i go to configure it?

---

### Post by jcbwalsh on 2007-03-25
Right click on the icon and you should see a menu item for VPN Connections. From there it should be very similar to setting one up from XP. 

James

---

### Post by g00s3m4n on 2007-03-25
hi again..

thats just it, i cannot find an icon..

i typed: sudo apt-get install network-manager-gnome and it installed ok.. where would the icon be?

---

### Post by g00s3m4n on 2007-03-26
hello again

i installed network-manager-gnome and network-manager-ppp and I have found the icons etc.. I have configured a vpn connection and I am still having problems getting it to work. it tries to connect and then says: "... due to a connection error".

anyone have any advice on where i can go to try and troubleshoot this? where are the log files kept?

thanks

---

