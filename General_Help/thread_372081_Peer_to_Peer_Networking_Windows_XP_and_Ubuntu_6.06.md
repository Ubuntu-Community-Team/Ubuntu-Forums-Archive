---
title: "Peer to Peer Networking Windows XP and Ubuntu 6.06"
date: 2007-02-27
forum: General Help
---

### Post by cde on 2007-02-27
I'm very new to the Linux operating system and I'm pretty unfamiliar with the Linux commands. Is there anyway to set up a peer to peer network between Windows XP and Linux using the Ubuntu GUI? I have the Windows machine configured how I would for networking to another Windows XP and Ubuntu seems to recognize my NIC. It allows me to configure it but I'm not entirely sure how to complete the setup. My hope is to share the Windows' internet connection through the network so I have assigned a static IP address in XP and made the same IP address a host in Ubuntu. What can I do now?

Any posts appreciated, thanks.

---

### Post by chewearn on 2007-02-28
> **cde said:**
> I'm very new to the Linux operating system and I'm pretty unfamiliar with the Linux commands. Is there anyway to set up a peer to peer network between Windows XP and Linux using the Ubuntu GUI? I have the Windows machine configured how I would for networking to another Windows XP and Ubuntu seems to recognize my NIC. It allows me to configure it but I'm not entirely sure how to complete the setup. 

One way is to use Windows networking to share folder.  On Linux side, this is called samba, and I belief it is already set-up by default in Ubuntu.
Myself, I came old school Win3.1, right up to WinXP, and was never very comfortable with the security of Windows networking; hence, I have locked up my Windows machine such that the networking feature is crippled.
I use plain simple ftp instead, or even sneaker net, if I need to share files between my machines.  Also, it means I unfamiliar with Windows networking setup.  Maybe someone else can give you a better answer.


>  My hope is to share the Windows' internet connection through the network so I have assigned a static IP address in XP and made the same IP address a host in Ubuntu. What can I do now?

Any posts appreciated, thanks.

To share you WinXP internet connection (I assumed you are using WinXP, else reply back), simply use the Windows internet connection wizard.  On the ubuntu side, just treat your WinXP machine as if it is a router, i.e. use its IP as Gateway and DNS.

---

