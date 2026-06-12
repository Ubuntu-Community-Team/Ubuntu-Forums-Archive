---
title: "How to establish a remote terminal session not knowing the target's ip/name?"
date: 2012-10-18
forum: General Help
---

### Post by s.v.z on 2012-10-18
Hi! I have an Ubuntu 12.04 PC with a dynamic IP address in a local network (192.168.x.x) behind a NAT. I want to have remote control of my PC. 

So far I've been using TeamViewer + Wine to get access to the PC desktop. The problem is that sometimes the connection I'm using is too slow or unstable to work comfortably with TeamViewer. 

I'd like to know if there is a similar solution that would allow me to gain access to my PC's console and support file transfer or even allow to pipe X? The problem here is that I have no idea of the machine's IP address.

---

### Post by CharlesA on 2012-10-18
If it is your own machine, look into dynamic DNS and then use ssh or the like to connect.

---

### Post by Insomn1a on 2012-10-18
[http://www.no-ip.com/downloads.php?page=linux](http://www.no-ip.com/downloads.php?page=linux)

This is a follow up on the previous post, try the link above, no-ip i believe has free accounts, and that is a linux dyndns client that will update your no-ip address with the ip of your computer if it ever changes.

---

### Post by s.v.z on 2012-10-21
> **Insomn1a said:**
> [http://www.no-ip.com/downloads.php?page=linux](http://www.no-ip.com/downloads.php?page=linux)

This is a follow up on the previous post, try the link above, no-ip i believe has free accounts, and that is a linux dyndns client that will update your no-ip address with the ip of your computer if it ever changes.

I suppose there is a bit of misunderstanding. With **no-ip** I can update my account with the IP-address of the NAT server which is of no big use. The machine I want to connect to is in the local network with a 192.168.x.x address and this makes **no-ip** and services of this kind quite useless.

---

### Post by Lars Noodén on 2012-10-21
You'll need to configure you "nat server" to forward an external port over to port 22 on  192.168.x.x address.  The exact details vary depending on make and model of your router.  That should be the final step, if you are getting a name from your dynamic DNS service.

---

### Post by s.v.z on 2012-10-26
> **Lars Noodén said:**
> You'll need to configure you "nat server" to forward an external port over to port 22 on  192.168.x.x address.  The exact details vary depending on make and model of your router.  That should be the final step, if you are getting a name from your dynamic DNS service.

I'd love to, but I have absolutely no access to this NAT and this makes things a bit complicated. And as I wrote in my first post, the 192.168.x.x address is a dynamic one.

---

### Post by Lars Noodén on 2012-10-26
As I see it there are three options.

The first, which you ruled out, is to use port forwarding on the router.

The second is probably also ruled out, which is to use the router as a jump host.

The third is a reverse tunnel, but that requires an external host to which you can connect to via SSH and stay logged in for a long while.

Maybe there's fourth option that someone can point to.

---

### Post by papibe on 2012-10-26
> **Lars Noodén said:**
> Maybe there's fourth option that someone can point to.
VPN, e.g., [LogMeIn Hamachi]("https://secure.logmein.com/") (there are several tutorials in youtube on how to do it on Ubuntu).

Regards.

---

### Post by CharlesA on 2012-10-26
> **papibe said:**
> VPN, e.g., [LogMeIn Hamachi]("https://secure.logmein.com/") (there are several tutorials in youtube on how to do it on Ubuntu).

Regards.
+1. TeamViewer might work too.

---

### Post by s.v.z on 2012-10-30
Will look towards Hamachi. As I wrote in my first post, I'm already using TeamViewer, but the GUI part of it is sometimes too slow.

---

