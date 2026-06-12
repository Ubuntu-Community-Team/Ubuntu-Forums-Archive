---
title: "How to change the last digits of my IP address?"
date: 2015-03-29
forum: General Help
---

### Post by BlackoutWorm on 2015-03-29
Hello.
I remember from Windows I was able to change the last part of my IP address.
Is this possible in Ubuntu?

---

### Post by ajgreeny on 2015-03-29
Are you asking about the LAN IP address, ie the one you get from the router you use, usually something like 192.168.1.2, or do you mean the WAN IP address which is the IP of your router which comes from the ISP you use normally,which could be almost anything, such as 95.146.139.178.

For the former, you can usually set that in the router, perhaps by IP reservation for the MAC address of the hardware, but I have no idea about how to change the WAN IP except that I know it can change if you reboot the router.

---

### Post by BlackoutWorm on 2015-03-29
I mean the one I get from whatismyip.com

---

### Post by Vladlenin5000 on 2015-03-29
> **BlackoutWorm said:**
> I mean the one I get from whatismyip.com

That's your WAN IP, obviously. As such, you don't change it. As said before, it may or may change anyway after rebooting the router but it's always assigned to you by your ISP. You can't change that from Windows or any other OS for that matter. What you MAY have been using in Windows is some VPN software/service. So, start by telling us what you do/did in Windows. Then we might be able to tell what's going on.

---

### Post by BlackoutWorm on 2015-03-29
Yes I am able to change that from windows. Only the last 3 digits though.
Like this:
[IMG]http://4.bp.blogspot.com/-SxioJGx1aig/UqXGGkVw2vI/AAAAAAAABCs/Lio6cQhMfHY/s320/How_To_Change_IP_Address_In_Windows_7.7.png[/IMG]
And no it doesn't auto change after reboot.
By using this technique, the ip changes on the fly

---

### Post by Vladlenin5000 on 2015-03-29
Your LAN (internal) IP is the one you can change with that tool. Usually the home router is also a DHCP server, ie, it assigns a dynamic IP for any device connected to it but some can explicitly choose a different, static IP, provided it is in the same "pool"...

---

### Post by BlackoutWorm on 2015-03-30
So is this possible on Ubuntu?

---

### Post by dragonfly41 on 2015-03-30
In my Ubuntu 14.04 ...

System Settings > Network > Options > IPv4 Settings

or in top bar click on ...

Network Connections icon (up down arrows) > Edit Connections > Ethernet > Connection > Edit > IPv4 Settings

---

### Post by Topsiho on 2015-03-30
Changing your WAN IP address (the one that is given to you by your provider) is the same as changing your telephone number.
My telephone number is x, but I make it y, and now nobody can call me.

Topsiho

---

### Post by TheFu on 2015-03-30
> **BlackoutWorm said:**
> So is this possible on Ubuntu?

Reconsidered .... you may be the ISP or using an assigned netblock from an ISP or hosting provider.  If that is the situation, you can edit the /etc/network/interface file OR if you have a GUI running, use that to alter the pre-existing static IP.

If you do not have a static IP already configured - it is DHCP - then it is a really, really bad idea to change it on the public facing connection.  

As a network admin, you can see below how made doing that would make me when (not if) I caught someone doing that.

Yes, you can, but if I were the network admin, I'd block you forever and never allow you back on my network. NEVER. Changing a public IP without approval like this is bad and can cause all sorts of network issues.

There are well-written guides for most of these questions.
* Desktop Guide: [https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)
* Server Guide: [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)
Sometimes these are not clear, so asking is always fine too.

---

