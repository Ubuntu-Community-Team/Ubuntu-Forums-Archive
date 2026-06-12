---
title: "ndiswrapper"
date: 2005-10-26
forum: General Help
---

### Post by 3dmaker on 2005-10-26
Hmm. I have installed ndiswrapper, and put it into my /etc/modules, so it loads and I dont have to modprobe it. But it takes really long on boot, and dosent load it. So I am wondering what is the way to disable its boot at load?

---

### Post by locutus42 on 2005-10-27
[QUOTE=3dmaker]Hmm. I have installed ndiswrapper, and put it into my /etc/modules, so it loads and I dont have to modprobe it. But it takes really long on boot, and dosent load it. So I am wondering what is the way to disable its boot at load?[/QUOTE]

you can hit "ctl-c" during boot to skip the networking setup when it hangs for too long.

when I switched to the wireless lan, I too would have to wait for-ever for the network setup to complete. Then, I found I could comment out the ethernet/wired LAN section so only the wifi network was setup. Now, the boot time is much lower when I'm around my WAP. here's what I did:

edit your /etc/networking/interfaces file and comment out the "auto eth0" and "map eth0" lines.

if you really want to just remove the ndiswrapper module loading, I think you can remove the /etc/modprobe.d/ndiswrapper file to do that.

---

