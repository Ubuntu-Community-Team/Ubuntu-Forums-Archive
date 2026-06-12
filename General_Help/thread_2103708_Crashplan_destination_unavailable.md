---
title: "Crashplan destination unavailable"
date: 2013-01-11
forum: General Help
---

### Post by gellpak on 2013-01-11
I got crashplan installed and running, and it's backing up my ubuntu machine to the cloud.

I also want to use the 'backup a friend' functionality to designate a folder on the ubuntu computer that my laptop can back up to.

However, when I designate a folder in the crashplan utility and watch the parent folder to see if the utility creates it, it never does. In the interface, it tells me 'Destination unavailable - backup location is not accessible'.

I've chmodded the parent folder 777 and the whole drive is owned by root. My only other thought is that I have to confirm that the group the crashplan service is a member of has access to that folder as well. How would I figure that out? 

Or, am I missing something else obvious? Perhaps I need to do some port forwarding or something? This is all inside my local network.

---

### Post by gellpak on 2013-01-11
Left it on overnight and it resolved itself. I assume it needed time to begin the backup process from my laptop.

---

