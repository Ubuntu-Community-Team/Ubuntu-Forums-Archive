---
title: "Samaba says folders on a vFAT don't exist"
date: 2006-10-28
forum: General Help
---

### Post by rianquinn on 2006-10-28
I setup my samba network, and for some reason the folders on my vFAT partitions do not exist. When you click my computer in the list of computers on the network you get a list of the folders, but when you click the folder samba says the folder doesn't exists.

---

### Post by rianquinn on 2006-10-28
Here is what I did to solve this problem,

rm -Rf /etc/samba/smb.conf

Then

   Re-Install samba via Adept/Synaptic

Finally I used KDE's samba configuration tool. Worked great.

What not to do

    Use Kubuntu's File Sharing Utility. Needs some serious work. I'm glad that you can still use KControl in Kubuntu for these reasons.

Hope this helps.:rolleyes:

---

