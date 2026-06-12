---
title: "[SOLVED] VMWare virtual machine setup"
date: 2008-06-21
forum: General Help
---

### Post by Stolea on 2008-06-21
I have installed VMWare Server and am trying to "Create a new virtual machine"
Everything is pretty self explanatory up to the point that I assign the location. The default is [COLOR="Blue"]/var/lib/vmware/Virtual Machines/Windows XP Pro[/COLOR]. /var is part of the root system and only has 26gig room to spare. I have 180gig room on /home, but when I try to set it up in [COLOR="Blue"]/home/vmware/Virtual Machines/Windows XP Pro[/COLOR it gives the following error :[COLOR="Red"]Unable to complete wizard: Unable to create a new virtual machine: No permission to perform this operation[/COLOR]
Any suggestions how to get around this?

---

### Post by doorman on 2008-06-21
Why not saving the file in [COLOR=Blue]/home/your_username/vmware/WinXp[/COLOR]?

Prior to creating a new machine you should make sure the given path exists

---

### Post by Stolea on 2008-06-21
I keep forgetting that Linux is case sensitive. I had created the correct directory, but got the case wrong. OOPS

---

