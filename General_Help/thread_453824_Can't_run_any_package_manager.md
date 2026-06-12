---
title: "Can't run any package manager"
date: 2007-05-24
forum: General Help
---

### Post by jbotello on 2007-05-24
Hi,

I only have a week using ubuntu, I basically using it right now for educational and self training purposes.  However, trying to install new programs have been a nightmare.  At the beginning everything was ok, but now every time I try to run any package manager, it just crash with the following error

jbotello@father:~$ sudo apt-get upgrade
Reading package lists... Done
[COLOR="Red"]E: Invalid record in the preferences file, no Package header[/COLOR]
jbotello@father:~$ 

Same happen if I run Synaptic gui.

I try some advices I found with goolge, like remove 
sudo rm pkgcache.bin
ssudo rm pkgcache.bin

but still have the same problem.

Someone have any other idea, how can i fix this?

regards,

---

### Post by jbotello on 2007-05-24
Yes, I found my problem.  My preference file at /etc/apt was empty.   I delete the file, and now the apt and synaptic is working fine.

just post my solution, may help others in the future.

regards,

---

