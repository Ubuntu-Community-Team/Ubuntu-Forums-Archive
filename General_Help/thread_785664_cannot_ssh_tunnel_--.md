---
title: "cannot ssh tunnel -- ?????"
date: 2008-05-07
forum: General Help
---

### Post by alphis on 2008-05-07
This is a strange problem that I'm not sure if it is specifically ubuntu or the version of ssh it comes with.

Basically I setup ssh tunnels to access VNC over untrusted networks. I've done this a billion times, and I do it still at work. However when I tried to do it on my ubuntu system ssh kept complaining about not being able to bind to the address.

So I specified the LAN ip of the wireless NIC which I thought was strange as I never needed to and it didn't error. However connecting to my LAN ip with the vnc viewer failed! It wouldn't connect. I can see the SYN SENT status for the port but no response! This does not happen with ANY of my other linux distros nor my cygwin ssh on windows.

What the hell??

Also, Im not sure if this is related but maybe, I've noticed that there is no loopback device....I've never _not_ seen the lo interface when doing an ifconfig -all. Maybe this is related? Maybe not? 

Any help is *very* appreicated!

---

### Post by Monicker on 2008-05-07
I haven't had any problems doing ssh tunneling with Ubuntu.  And I know others on these forums are doing it.

Your lo interface should definitely be up.  What are the contents of /etc/network/interfaces?

In /etc/ssh/sshd_config, the default is to listen on all interfaces.  Has that been changed?

---

### Post by davidpbrown on 2008-05-07
Probably I'm way off, cause this is obvious and you evidently use it more than I do, but I had a problem since upgrade to Hardy with the SSH port not being open.. adding [Allow Service SSH Port 22 For Everyone] to Firestarter::Policy had me back up and running.

---

### Post by alphis on 2008-05-09
Thanks for the responses. I've checked the /etc/network/interfaces file and it confirmed the lack of a loopback interface. There is only ath0 and some essid information for the network I connect to.

The other file, sshd_config didn't have anything in particular that was interesting in it. Needless to say I never tampered with that file.

Any ideas as to why I can't ssh tunnel? When I create the tunnel, as I always do at work at home at ANYWHERE, I can see via netstat that the usual ssh port and the port I'm forwarding are both listening. Its just when I connect that there is no response. I think its an interface issue which is why I suspect the loopback device being missing as the culprit.

Any ideas?

---

### Post by KillaB7 on 2008-05-11
Not sure yet how to do this at the CLI, but I have the same problem using PuTTY in Hardy.

I have XP set up in VMWare and tunneling with PuTTY through the VMWare Ethernet bridge works fine so I'm not sure where the problem is?

---

