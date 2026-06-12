---
title: "Server unexpectedly shuts down intermittently"
date: 2024-09-26
forum: General Help
---

### Post by per42 on 2024-09-26
I have an Ubuntu 22.04.1 LTS (GNU/Linux 5.15.0-122-generic x86_64) running my mailserver (Axigen) on vmware ESXi 6.5.0. 
Now and then the Ubuntu server shuts down. I can't find any reasons in any Ubuntu logs (but I am not really sure where to look). vmware logs an event saying "The CPU has been disabled by the guest operating system. Power off or reset the virtual machine. ".

This happens intermittently but more often when I am on holliday and don't check mail as often. This makes me think there is a hibernation thing, that the OS shuts down when it's been idling a while. But sometimes it shuts down anyway. Yesterday it did so between sending two emails. 

I have googled and tried several solutions both with vmware and Ubuntu, but none have adressed my problem exactly and non have worked. And no, unfortunately, I cannot list exact what I have tried as it was a while ago and I don't remember exactly what I did. 

Any suggestions?

---

### Post by TheFu on 2024-09-26
> VMware officially declared vSphere 6.5.x and vSphere 6.7.x End of Support Life on November 15th, 2023.
Move to a supported hypervisor version is the easy answer.

That's the first thing to do.

Look over the system logs. A server shouldn't be allowed to hibernate or go into standby mode.  That certainly isn't default behavior, so if that's happening, something you did enabled it - perhaps a GUI was installed?  Just a guess.

---

