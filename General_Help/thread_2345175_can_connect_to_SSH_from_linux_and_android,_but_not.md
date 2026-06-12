---
title: "can connect to SSH from linux and android, but not from windows"
date: 2016-12-01
forum: General Help
---

### Post by mbkfa93 on 2016-12-01
Hi. I have ubuntu-server-14.04 x64 installed on a desktop pc, and i'm using it mainly as a local file server. It's got a static IP and it's working fine. but SSH is not working when i connect from windows.
i can connect normally from linux (Kubuntu 14.04) on my laptop, and even from android from juice SSH without a trouble. the problem is when i try to connect using putty on windows, it doesn't work. I tried other alternatives to putty like Bitvise SSH client, but still the same thing.
Putty and bitvise work fine on ubuntu server in vbox, but not with the desktop.
ping works both ways between the laptop and the desktop. I tried from a different laptop but still the same thing.

i tried reinstalling openssh-server, but still the same results

i'm really confused, the network connectivity is fine, the desktop is fine, and my laptop is fine.
so, what is exactly the problem here?

i'd really appreciate any help

Thanks

---

### Post by kpatz on 2016-12-01
What error message do you get from the windows client?  Maybe the windows firewall is blocking the connection?

---

### Post by kingneutron on 2016-12-01
--Also post whatever antivirus software or "protection" software you have installed, those could be in the mix preventing connection...

---

