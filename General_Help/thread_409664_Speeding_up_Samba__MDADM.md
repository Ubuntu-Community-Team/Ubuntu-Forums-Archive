---
title: "Speeding up Samba / MDADM"
date: 2007-04-14
forum: General Help
---

### Post by gobuchul74 on 2007-04-14
I've recently changed over my file server to Ubuntu.  I have two raid 5 arrays using Mdadm with all my movies on them.

My problem is copying movie files to the server is very slow and is causing pauses during playback if I'm watching a movie while writing a file.

I'm not sure if this is a networking issue (everything is run on wired gigabit cards) a Samba issue or a Mdadm issue.

When writing a file through the network the CPU load rarely exceeds 8%, so I don;t think Mdadm is having a problem making the raid calculations.

Is there any way you can think of to figure out the root cause, and/or correct the speed issue?  Is there some way to raise the priorities of Samba/Mdadm?

---

### Post by gobuchul74 on 2007-04-15
I think I've answered my own question, but I'll post it here in case anyone else has the same issue.  My motherboard has the Attansic L1 gigabit ethernet device.  The drivers for this device in Linux are not so hot and until Feisty I hadn't seen a distro that included them.  The problem is slow transmitting of data.  Apparently it will also cause the server to slow up when sending data to other computers while I'm copying files to the server.

I guess I'll switch to a pci ethernet card.

---

