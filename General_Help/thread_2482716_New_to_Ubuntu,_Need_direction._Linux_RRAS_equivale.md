---
title: "New to Ubuntu, Need direction. Linux RRAS equivalent?"
date: 2023-01-09
forum: General Help
---

### Post by nickisabi on 2023-01-09
Hi, all. I'm really new to Ubuntu and GNU/Linux in general. I'm running a couple Ubuntu desktops and 3 Ubuntu server VMs in Hyper-V. On my school's VM server, in an all-Windows design, I was able to set up a domain controller, 3 clients, and then 1 server with Routing and Remote access to connect the virtual network to the external network and make the internet accessible to the clients. I'm trying to do something similar with Ubuntu. What I want is 2 desktops and 3 servers connected on one virtual switch. The third server is connected to the internal virtual switch named "Ubuntu.net" and then on a different interface, I want it to connect to the external virtual switch that connects to my computer's Ethernet adapter out to the router and then the internet. This way, I can have all my Ubuntu stuff on a virtual network inside Ubuntu.net that can also access the internet via a bridge. I'm not too well versed in this topic, and I only know how RRAS works. I'm not sure what the Linux equivalent is, let alone how to configure it. I keep getting Google results about VRF being a thing? Is that what I should use to accomplish this task? If so, can someone direct me to where I can learn how to configure that?

I appreciate you guys taking the time to help me with this.
-Nic

---

### Post by dragonfly41 on 2023-01-09
I always find when I pickup a discussion in this forum I learn a few points myself.
I too am interested in orchestrating various resources as a "testbed" (proof of concepts)
including remote desktops and server instances.
And so in hitching onto your question I found this .. for starters ..

[https://ubuntu.com/engage/microsoft-active-directory](https://ubuntu.com/engage/microsoft-active-directory)

Blind leading the blind.

---

