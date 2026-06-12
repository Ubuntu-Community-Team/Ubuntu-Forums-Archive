---
title: "VFS: file-max limit"
date: 2006-11-14
forum: General Help
---

### Post by cri on 2006-11-14
I'm running Kubuntu Dapper, kernel 2.6.15-23-686, on a Dell e1405 with 1.5GB of RAM. Lately, while coding with IntelliJ, I'll occassionally start getting "too many files open messages" and then the system just goes downhill. Posts to web forms in my open browser won't work. Applications won't open (not even a shell!). I can't login to a virtual console. Basically anything that requires opening a file fails. I am forced to reboot. These are the only interesting messages I see in my logs:

Nov 13 03:27:48 localhost kernel: [4309438.213000] VFS: file-max limit 152386 reached

Google searching suggests I should upgrade the kernel. From what I can tell with Adept, there is no newer kernel for Dapper available. I could upgrade to Edgy but I'm reluctant to do so since I'm seeing bad reports about upgrades and I can't risk it as I use this machine for work. 

Anyone have any resolution to this problem short of rolling a new, custom kernel?

Thanks.

---

