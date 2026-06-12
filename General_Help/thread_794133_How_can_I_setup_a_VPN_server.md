---
title: "How can I setup a VPN server?"
date: 2008-05-14
forum: General Help
---

### Post by TidusBlade on 2008-05-14
I currently have a server with Ubuntu 6.06 LTS Server edition it, but I'll be upgrading to 8.06 LTS Server soon.
Anyways, I was wondering if there is any way I can setup a VPN server on the server, and use the VPN server to bypass blocked sites on my end. (My ISP is crazy, blocking Flickr and such xD) So basically I want to be able to browse the internet though the server...

Any suggestions warmly welcomed =]
Thanks!

---

### Post by jimv on 2008-05-14
You don't want VNC.  You want an SSH tunnel.

EDIT: LOL, you said VPN, not VNC....oops, my bad...but the answer is still the same.

Allow me to elaborate.

An SSH tunnel establishes a secure connection with your home machine.  A port is opened on your local machine that you can send traffic through, like a proxy.  When you send traffic through that port, your home machine goes out and gets the data, and send it back to you through the same port.

Are you using Ubuntu on both machines?  If so, see this guy:
[http://wiki.freaks-unidos.net/weblogs/azul/firefox-ssh-tunnel](http://wiki.freaks-unidos.net/weblogs/azul/firefox-ssh-tunnel)

That's how to set up a tunnel with the command line.  Once you have that figured out, there's a gui to manage your SSH tunnels called Gnome SSH Tunnel Manager:
[http://www.ubuntugeek.com/manage-ssh-tunnels-with-gnome-ssh-tunnel-manager.html](http://www.ubuntugeek.com/manage-ssh-tunnels-with-gnome-ssh-tunnel-manager.html)


OH YEAH, make sure you have openssh-server installed on your server, and port 22 (SSH uses this port) forwarded through your router to the server.

OH YEAH YEAH, you should also setup your router with a Dynamic DNS (DDNS) service like DynDNS.com   What that does is gives you a domain name instead of an IP for your home connection, and allows your router to update where the domain name points if your ISP changes your IP.  If your router doesn't come with a function to do DDNS, you may want to look into upgrading your router with DD-WRT firmware....basically it turns a $50 router into a $500 router.

---

### Post by TidusBlade on 2008-05-14
Thanks for the quick reply =]
Well I always hear VPN so I assume it was that...

Anyways, Ill try the links you gave me, they seem useful ^_^
And by the way, running Gentoo on my local machine so I'll just have to edit a few stuff and the server has no GUI, but SSH is there and fully working =]

---

### Post by jimv on 2008-05-14
> **TidusBlade said:**
> Thanks for the quick reply =]
Well I always hear VPN so I assume it was that...

Anyways, Ill try the links you gave me, they seem useful ^_^
And by the way, running Gentoo on my local machine so I'll just have to edit a few stuff and the server has no GUI, but SSH is there and fully working =]

VPN was right....VNC is remote desktop stuff....not even close to what you meant, lol.  I need more coffee.

If you've got SSH set up on your server, and you can SSH into it from your Gentoo machine, you're all set.  I would imagine that the Gnome SSH Tunnel Manager will work fine in Gentoo if you're using Gnome.

And one thing that took me awhile to figure out when using Gnome SSH Tunnel Manager...so you set it up to connect to your server, and in the bottom section is a 'Port Redirection' section.  If you want to forward all your Firefox traffic, add a redirection, and choose 'Dynamic' for the type, and set the port to whatever you want.  I chose 12345.  Thats the port you'll set for your socks5 proxy in Firefox.

---

### Post by talz13 on 2008-05-14
And if they're mean and block all your outgoing ports, try forwarding on port 443 (https port), since they most likely won't have that blocked.

---

