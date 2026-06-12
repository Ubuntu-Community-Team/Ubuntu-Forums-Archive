---
title: "Unusual networking setup.lol..Wireless Dialup."
date: 2006-07-09
forum: General Help
---

### Post by Patrick-Ruff on 2006-07-09
hey all, I'm trying to get a strange network setup going. see, the Windows computer, shall be the host, that is using ICS. I'm trying to set this up with a wireless router, :P. 

The wireless router is a ENCORE ENHWI-G2 (pretty much the same as the G but black). 

The Linux laptop, will merely be getting internet off of the host computer, the windows ICS desktop, which is dialing up and connecting directly to the internet, and it is hooked up to the LAN1 port.   How should I have my router configured to conform to ICS's settings? ICS uses IP 192.168.0.1, my router (factory defaults) is using 192.168.1.1, right now I have it set up to Bridged Mode, DCHP disabled on LAN, etc.


however, I am unable to access the internet on the laptop :(. I'm pretty sure the router is getting in the way tho, since I tried it on both operating systems on the laptop, neither worked. how should I have my router configured to conform to such things? I know this is /slightly/ windows related, but, the router is merely networking protocals and such, which should be multi-OS knowledge :).

so if you guys have any knowledge of this, or successfully did a similar setup to this one, please feel free to reply.

---

### Post by Patrick-Ruff on 2006-07-09
yo, I could use an answer before this thread goes a few pages back :(.

---

### Post by joft on 2006-07-10
Hi,

I am not an expert with ICS, but I suggest using the same subnet for all components of your network (Windows machine, Router, Linux Laptop).

So, if ICS doesn't allow you to change the internal IP address of your Windows machine (192.168.1.1), you can start by changing the Router's IP to something like 192.168.1.2 (=> change factory default).
And since you disabled DHCP on your Windows host (Is ICS coming with a DHCP server?), you should either have DHCP enabled on your Router, so that the wireless Laptop gets an IP or configure your laptop with a static IP (e.g. 192.168.1.3).

Then you have to make sure, that the default gateway of your laptop is pointing to your Windows machine. This can be done by either telling the Routers DHCP server to provide 192.168.1.1 as the default gateway or configuring your laptop manually (static) with that IP as default gateway.

At the end, you have to check DNS settings - your laptop has to know the IP of some DNS server. This can be done in the same way as above (default gateway). (Does ICS come with a DNS (proxy)?)

---

### Post by bigken on 2006-07-10
not to sure but in concetions select your dail up icon right click and select
properties /advanced and allow other network users to conect to the internet ;)

---

### Post by Patrick-Ruff on 2006-07-12
lol bigken, I appriciate the attempt, but that is a useless post since I have obviously gotten past that part, and its into another more complicated section :P

---

### Post by bigken on 2006-07-13
:mrgreen:

---

### Post by Patrick-Ruff on 2006-08-19
ok I know this thread is insanely old but it appears the only way I've been able to pull off this setup is with the desktop being a proxy server...the problem is, Freenode IRC doesn't allow proxy's, and you really can't do /as/ much with them. does anyone else have any alternatives for me?

---

### Post by bensexson on 2006-08-19
Ensure NAT is disabled on your router.  Can you get an IP address from the windows box?  If you connect directly to the windows box does it work?

---

### Post by Patrick-Ruff on 2006-08-19
yes yes. I have static IP on and all that, NAT is off of course, etc. the entire network is static IP based.

---

### Post by bensexson on 2006-08-19
The problem is probably ICS.

---

### Post by Patrick-Ruff on 2006-08-19
lol obviously...what I need here is an alternative program or a remedy.

---

