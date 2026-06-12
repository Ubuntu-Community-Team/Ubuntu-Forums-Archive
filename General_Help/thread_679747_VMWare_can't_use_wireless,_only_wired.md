---
title: "VMWare can't use wireless, only wired"
date: 2008-01-27
forum: General Help
---

### Post by TechnoJunky on 2008-01-27
I suppose I setup my VMServer while connected to the wired network on my laptop.  I definately built my VM XP while connected to the wired network.  The problem is that I can't connect to the network using the wireless nic on my VM XP.  I've tried running the install script again while using the wireless nic, but still no go.  If I had to choose between alway using only the wired or only the wireless, I'd prefer the wireless.  Is there anyway to tell VMServer to use the wireless nic?

---

### Post by MoLE on 2008-02-03
How have you set network manager up?  Can I suggest disabling the wired connection while you are using wireless before launching the VM?
VMware server shouldn't care about how you're connected to the internet, so probably an Ubuntu problem.

Which version of Ubuntu are you using?

---

### Post by PaulSipot on 2008-02-03
I had the same problem, the thing is that you need to create a bridge interface from your wireless interface which I couldn't do for some reason with madwifi which I was using, see with your wireless driver if you can create a bridge interface, then if it works setup vmware for that.

---

### Post by -Vampyre- on 2008-02-04
I could never get bridged networking to link to the wireless, only to wired. To get the Virtual machine to work through the wireless, I had to set it to be a NAT interface.

---

### Post by iThinkergoiMac on 2008-02-23
I'm having a similar issue. I have an IBM R50 with the intel Pro/Wireless built-in card, and VMWare Server doesn't want to recognize it. When I go to set up the network in Windows, I don't have the option for wireless at all.

It's set to bridged, and isn't giving me any errors. Any ideas?

---

