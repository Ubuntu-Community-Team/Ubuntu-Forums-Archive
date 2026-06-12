---
title: "Documentation on &quot;secondary groups&quot;"
date: 2007-12-24
forum: General Help
---

### Post by Kjella on 2007-12-24
Running Kubuntu 7.10, where can I find some documentation on what the different secondary groups (admin, lpadmin, audio, cdrom, plugdev etc.) do exactly? The help is empty and couldn't find one searching with google either. Some are sorta obvious, others are not at all.

---

### Post by p_quarles on 2007-12-24
It's set up this way to separate processes from one another. Basically, each of these non-human users are responsible for running some aspect of the system. Separating them ensures that if one breaks down (or, worse, gets compromised somehow), it doesn't bork the rest of the system. 

Each user also gets a group automatically associated with it. Again, this is useful for security and stability: it allows you to add human users to individual groups, giving them the ability to do certain things (like load a music CD, or or safely shutdown the computer) without granting them the power to mess up the whole system. 

As for what the non-obvious ones do: lpadmin runs your printers, plugdev is responsible for a range of hardware devices, and admin consists of users who are given the right to run as root using the "sudo" command.

---

