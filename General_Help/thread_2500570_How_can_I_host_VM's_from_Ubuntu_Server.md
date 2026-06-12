---
title: "How can I host VM's from Ubuntu Server?"
date: 2024-09-05
forum: General Help
---

### Post by garnold on 2024-09-05
I've just setup an Ubuntu Server and now I'm trying to add all the tools I'd like to use on it. I've installed Docker on this box to handle my containers and will admin this with Portainer. I've also installed Webmin to be my web based front end to this headless server (never knew about this tool, very cool!!). Now I'd like to tackle VMs. Normally I would just install Virtual Box on the machine and be good to go. Since this is headless I do not have a GUI to handle this. I really liked how Proxmox allowed me (when testing that tool) to spin up and run VM's right from a web interface and actually run their GUIs from the web. Another thing I never knew about (so much to learn). Is there some method to allow me to spin up VMs on this server from the web and manage them via a web site? I don't need Proxmox at this point but that is basically what I'm looking for. Thank you!

---

### Post by ian-weisser on 2024-09-05
Lots of ways. VirtualBox headless, LibVirt, QEMU/KVM, LXD. They can all run VMs from a headless server.

Personally, I use LXD/Incus simply because it makes sense to me. I can maintain it, back it up, rebuild it, and restore from backup in a way that feels right to me.

I don't know which method feels right and maintainable to you. Try them all, decide for yourself.

---

### Post by garnold on 2024-09-05
I'll totally check into these tonight. Do they all have some kind of web front end so I can deploy VMs from my other machines? Again, I'm not looking for Proxmox right now even though I'm referencing it a few times. What I liked about Proxmox we that I could create VMs from a nice interface from another machine and manage them all remotely. If the VM had a GUI you would see that from this noVNC web page. Really sorry if these are basic questions that seem pretty obvious to others. I'm still learning a lot here.

---

