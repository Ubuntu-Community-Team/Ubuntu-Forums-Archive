---
title: "Can remote desktop behave like RealVNC?"
date: 2024-11-10
forum: General Help
---

### Post by chr1sM on 2024-11-10
Hi,

I decided to stop using RealVNC and am finding the built in tools for remote desktop very limited. Is there a solution to remote into a Ubuntu 24.04 desktop if the user I am connecting with is logged in and does not require any user response from the connecting desktop? I guess I want to have a RealVNC experience without having to spend hours configuring my own vncservers.

Ironically, getting Apache Guacamole setup on a docker container in Ubuntu was easy. Currently I am connected to the desktop I want to connect to using ssh. I did not think the remote desktop connection would be the challenge :-)

Thanks,

Chris

---

### Post by TheFu on 2024-11-11
On the same LAN, no need for a remote desktop.  Just run the program you want using an ssh tunnel with X/Windows forwarding.  This assumes a Linux workstation that you are typing on.

Over a WAN connection, bandwidth limitations usually make remote X11 perform poorly, so other solutions like using a SOCKS proxy via ssh or using a full VPN to the remote LAN, but still using your local workstation for processing would be preferred if you are currently in a "safe" part of the world.

Sometimes, you might end up in a part of the world where you don't want ANY data on your local computer, so a remote desktop is the best possible solution. For that, I use x2go which is a free implementation of the NX protocol.  However, NX doesn't work with Wayland, so you'll need to keep using Xorg (perhaps on both the client AND the server) to ensure it works.

I was just looking at Guacamole setup yesterday. I'd looked at it around 2010 and decided I didn't like some of their application architecture choices.  Those choices still exist, which make me not trust the security of that tool.  Plus, since they stopped making .deb packages and maintaining their PPA for currently support Ubuntu releases, it is just too much hassle for me to try. I don't use Docker for containers for a number of reasons.  I do use Linux Containers, so it isn't the technology, but the default way that Docker containers are made. I suppose those defaults may be altered, but Guacamole still requires a java app server.

Anyway, Guacamole connections can be TLS encrypted over HTTPS. That doesn't authenticate sufficiently to me, but it does ensure that communications between the client and server aren't altered.

You could use and ssh connection as a SOCKS proxy into the remote system and allow Guacamole to only listen on localhost. In this way, you'll ensure the connection to the network is authenticated BEFORE any Guacamole authentication is attempted.  Similarly, you could use a VPN for the same purpose ... but allowing ssh or VPN into a Docker container is an anti-pattern for Docker security.  If any docker container allows running a VPN, then you can be 100% certain they are running a privileged container, which is a terrible practice and removes 95%, perhaps more, of the security any linux container provides.  We always want to use unprivileged linux containers for the best security.

Does any of this make sense?

---

