---
title: "VPN Help"
date: 2005-07-18
forum: General Help
---

### Post by diffuser78 on 2005-07-18
I need to connect to my workplace using VPN. I am not too sure what progrma to use in Ubuntu. I tried VNC with no success.

Can somebody tell me some easy to use program to use for VPN,

Thanks

---

### Post by amohanty on 2005-07-18
>  	I need to connect to my workplace using VPN. I am not too sure what progrma to use in Ubuntu. I tried VNC with no success.

Can somebody tell me some easy to use program to use for VPN,

Thanks 

It all depends on what VPN server/appliance your workplace uses. Most servers/appliances, even though they are built on Linux, do now allow direct connections via an SSL tunnel, go figure... 

Usually they require a windows registry edit (ask your system admin at work about this), and then an ActiveX client install via IE (from a seciure WAN site - again ask your admin) before allowing you to connect. Not true for all of them, but AFAIK most require such stupidity. So there are three possible ways you can do something:

1. Install Wine, IE6 and then do what is mentioned above.
2. Most of these appliances also allow for a java based VPN client. However your workplace' appliance needs to have this module. Again ask your admin if they have this. If they do then hunt down the client for it.
3. [this is an in your dreams.. suggestion] Ask your admin to open up your workstation for remote desktop, then use rdesktop.


HTH
AM

---

