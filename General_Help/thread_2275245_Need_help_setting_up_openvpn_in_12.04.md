---
title: "Need help setting up openvpn in 12.04"
date: 2015-04-25
forum: General Help
---

### Post by bobmac on 2015-04-25
Folks,

I've been trying to install openvpn but having no luck. I've hunted the web and tried to follow instructions but so far each time I've ended up stuck. Similarly, I've tried several tutorials with the same result.

Being somewhat technically challenged, I'm obviously doing something wrong.

Can anyone help set it up in laymans language?

I would grateful for any assistance.

Regards,

Bob

---

### Post by TheFu on 2015-04-25
openvpn is non-trivial to setup due to the thousands of different options available to provide a solution for organizations of any scale 1 to 20,000.  If you are technically challenged, perhaps using ssh for tunnels would suffice? ssh is 1000x easier to setup than openvpn.
[http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh) has a list of things that ssh can do. I think you'll be amazed.

If you post exactly what you plan to do with openvpn, I might be able to suggest ssh-based alternatives for a small group of people to use.  If you are hoping to get your non-technical wife to use ssh, don't think that will be likely, but for anyone choosing to run Linux, it is very easy.

---

### Post by The Cog on 2015-04-25
As TheFu says, please explain exactly what you are trying to do with openvpn. If it's anything like we use it at work, I can provide sample config files. But I do need good detail of what you are trying to do.

---

### Post by bobmac on 2015-04-25
Folks,

I'm trying to make sure that my data can't be scrutinised intruders.

Regards,

Bob

---

### Post by TheFu on 2015-04-26
OpenVPN doesn't do anything to help that when the data leaves your network.  For that you need an external VPN with an end-node in a different country and you/we need to be extremely careful not to leak personalized data. OpSec is hard.  I've heard of free VPNs, but I'd probably pay $4/month for one if I cared enough.  The provider would be using IPSec-based openvpn and they would provide me with a client configuration file. I could use this from home or when out and about.

The first time I connected to an external email/fb/twitter/photo/whatever account - that's it. The VPN exit traffic would be tied to me. It works the same way if I used TOR too.  OpSec is hard.

For my access back into my house when out and about, I generally use ssh. For 1 person, this isn't hard.  sftp provides secure access to files inside my network. ssh provides shell access or the base for NX if I need a remote desktop back to the house. Does this make sense?  sftp is built-into every Linux file manager. Just use sftp:// in the URL (if you are a GUI person).

---

