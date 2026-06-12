---
title: "Server 16.04 No network after reboot by ssh"
date: 2018-05-28
forum: General Help
---

### Post by patdundee on 2018-05-28
Hi Guys
As above
Log into Ubuntu Server via SSH and issue reboot which is ok

After reboot the Network does not come back up and I have to log in direct on the machine and reboot again. Then network comes up.

Seems everytime I reboot via SSH there is no network but the system starts up fine

Any ideas?
Many thanks

---

### Post by SeijiSensei on 2018-05-28
Does the server have a wired connection?  Does it have a static IP address configured?  Servers need hard-wired connections and fixed IP addresses to function effectively.  No wifi, and no DHCP.

---

### Post by patdundee on 2018-05-28
Hi Seiji
As a working server it would never be on WiFi. Static IP hard wired everytime is is rebooted remotely (especially after any updates) it fails to bring the network back up unless you access direct as mentioned above. I have several other Ubuntu servers (16.04) and this is th eonly one with the issue

---

### Post by SeijiSensei on 2018-05-29
i can't imagine any reason for this symptom.  Just to be clear, if you log in with SSH and issue the command "sudo reboot" it comes back up with no network connection at all?  I have no idea why this would be the case.  I've used Linux for many years now; I've never seen this problem.

Is there a way to look at the machine's state after a remote reboot?  Does ifconfig show that adapter is active but has no IP, is not detected at all, or is detected but not activated?

---

### Post by btindie on 2018-05-30
Are you running a desktop on that server? The only thing I can think of is NetworkManager is controlling your network and it's not applying the settings until you physically log into the desktop instead of having systemd configure it.

If you log into a terminal "Ctrl+Alt+F1" after a reboot, what's the output of *ip addr show* ?

---

