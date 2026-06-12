---
title: "dpkg: unable to create '/var/lib/dpkg/updates/tmp.i': No such file or directory"
date: 2012-11-26
forum: General Help
---

### Post by siafulinux on 2012-11-26
Note: I searched for this error in the forums before making this thread but was only able to find it in the archives. Decided a new thread would be warranted. 

Anyway, I installed an Ubuntu variant onto a USB thumb drive and one of my kids removed the drive while doing an upgrade. No installs would continue as I received the following error:

> dpkg: unable to create '/var/lib/dpkg/updates/tmp.i': No such file or directory

I searched for a solution and nobody seemed to have found one but I think I may have as my upgrade is now continuing. 

Here's what I did:

> 
sudo mv /var/lib/dpkg/updates /var/lib/dpkg/updates2
sudo mkdir /var/lib/dpkg/updates
sudo dpkg --configure -a


This seemed to have fixed the problem. I guess I could have simply removed the 'updates' folder instead? Hope this helps those having the same issue.

---

