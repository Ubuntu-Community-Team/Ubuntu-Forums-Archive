---
title: "NFS boot problems"
date: 2008-03-12
forum: General Help
---

### Post by Alien.col on 2008-03-12
Hello:

I installed the network drivers on my pc today so i could share some files. Ubuntu automatically installed some NFS packages there i think.

I went to start the computer and it took incredibly long to boot. It finally booted after 5 minutes or so. Afterwards i was able to activate the text messages and the system seemed to hang when it started the nfs kernel. I then proceeded to uninstall nfs-kernel-server, nfs-common and a nfs library. It worked! the hang at boot disappeared.

Now i'm worried about what I uninstalled, my question is what is nfs and what do i need it for???? 

Thanks

---

### Post by Alien.col on 2008-03-12
Bump! Anybody know what happens if i uninstall nfs????

---

### Post by fragos on 2008-03-13
NFS protocol is only used for network file access between Linux system.  Nothing else I can think of should be disabled by uninstalling.  The problem was likely a configuration issue or an attempt to access or mount a file on a non-existent IP.

---

### Post by Alien.col on 2008-03-13
Thanks for your answer, i guess that until i really need NFS i wont install it, i only need to transfer files via shared folders and that seems to work fine.

---

