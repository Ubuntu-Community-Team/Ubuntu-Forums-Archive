---
title: "network wants password"
date: 2017-05-14
forum: General Help
---

### Post by jgw on 2017-05-14
My network used to start on boot.  Then I added a vpn connection and, now, after boot it always asks for a password before booting.  The password request is for my ubuntu password and not the vpn password.  I am using the usenetserver vpn.  I have examined both the the ethernet (wired) and the vpn connection and everything looks right although I suspect I am missing something.  I have also read a suggestion to create a usenetserver.conf and a login.conf file at etc/usenetserver but before I start that I need to know if this is right.

Thank you...................

---

### Post by TheFu on 2017-05-14
I think this [https://askubuntu.com/questions/32164/what-does-a-keyring-do](https://askubuntu.com/questions/32164/what-does-a-keyring-do) explains what is happening.
[https://askubuntu.com/questions/10683/why-does-network-manager-always-ask-for-my-keyring-password](https://askubuntu.com/questions/10683/why-does-network-manager-always-ask-for-my-keyring-password) is a little old, but might be helpful.

I don't know that specific VPN, but if it is openvpn-based, then yes, you can make a login.conf file with your VPN login and passphrase that would be referenced in the .ovpn file, so you'd not be asked for a password.  Please check that your VPN isn't using PPTP, if you care about security at all.  PPTP has been hacked for about 15 yrs to the point that it is useless for anyone who cares about security.

---

### Post by jgw on 2017-05-15
Thank you for the reply. 
I read the stuff you suggested but it doesn't give me specific instructions.  I did, however, find something that may have something to do with it all.  IN theory it checks the network-manager and displays results:
 wpa_supplicant -D wired -i eth0 -c /etc/wpa_supplicant/wpa_wired.conf
Successfully initialized wpa_supplicant
Failed to open config file '/etc/wpa_supplicant/wpa_wired.conf', error: No such file or directory
Failed to read or parse configuration '/etc/wpa_supplicant/wpa_wired.conf'.

The reason I found that interesting is that it for a wired connection.  I now suspect it never even gets to the vpn but hangs when it hits the network-manager  for reasons other than the vpn as this seems to be a problem anyway.  There was also stuff about setting up the network in which it will constantly ask for password unless all users can connect is checked (it is, in both the wired (ethernet) and the vpn both have the all users thing checked).  I did notice the device address had two options; E0:3F:49:AD:2E:0A and enp2s0 (E0:3F:49:AD:2E:0A)     The first is checked, I have no idea where the second came from (i don't normally deal with this stuff).  

Anyway - I continue to be stuck.  

Thoughts?

---

### Post by TheFu on 2017-05-15
I don't use network manager or the manual wpa-supplicant stuff.  No ideas on that.
I use an openvpn-based VPN, but it isn't always enabled, so I run a script that brings it up or down as I need.

Don't think identical MACs can be on the same subnet. That would break ethernet.

---

