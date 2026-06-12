---
title: "Lubuntu 18.04, problems loging in with Teamviewer 15"
date: 2020-10-19
forum: General Help
---

### Post by macdummy on 2020-10-19
Hi, my first post.

I have a Lubuntu 18.04 machine, I have installed Teamviewer 15 (free) and it is working well however, when the screen is locked or when the log-in screen is up, I cannot access remotley via Teamviewer.   

PC is showing in the list of 'my computers' on Teamviewer however I cannot connect until I get someone to log-in at the other end.  Any ideas?

I have searched and seen mentions of Wayland/LXDE desktop issues.

---

### Post by TheFu on 2020-10-21
Don't use teamviewer? I've never used it for a few security reasons.

Instead, use **ssh** or **x2go**, which requires ssh to work.  After all, ssh is how Unix systems securely communicate and xfer files anyways. If you'd like help setting these up, let me know and we can get you setup for secure connections with ssh and all 50+ ssh-based tools like rsync, x2go, sshfs, scp, sftp, and the list goes on and on.

For remote desktops, x2go is the most secure and fastest solution that is suitable for use over the internet, without also having to use a full VPN solution.

But it is completely up to you.

---

