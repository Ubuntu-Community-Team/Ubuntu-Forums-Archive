---
title: "No Login Screen need to always go in to recovery mode"
date: 2019-06-15
forum: General Help
---

### Post by takeawaydave on 2019-06-15
Having trouble with Ubuntu 18.04 - It was working fine then updated the other day and doesn't work as normal - at least I think this is what happened.

Basically its a VM running on ESXi and when it starts up it boots but doesn't show the Login screen. I then restart it with either the VM Option "Restart" or SSH  in to the VM and reboot. Then I enter in to Recovery Mode and I can start networking and then resume and I get to the log in screen.

What could the problem be ? The kernel log seems to be clean with no unexpected errrors. All packages are up to date. No Disk space issues either.

Really don't feel like reinstalling - the weather is way too nice to be inside today!

---

### Post by cruzer001 on 2019-06-15
> It was working fine then updated the other day and doesn't work as normal - at least I think this is what happened
Even though your not seeing any unusual kernel errors you should try booting with the previous kernel.

---

### Post by easy-when-it-works on 2019-06-16
Had the same or very similar issue.  Mucked about for ages trying to get it working again.  Loads off different things tried etc.  Hopefully no chaos caused.  Settings fiddled with, packages added, removed, reconfigured etc.  Many hours burnt.

Eventually came to this post: [https://askubuntu.com/questions/1068809/no-login-screen-after-ubuntu-18-04-update](https://askubuntu.com/questions/1068809/no-login-screen-after-ubuntu-18-04-update)

With the   [COLOR=#242729][FONT=Consolas]WaylandEnable=false   fix, which seems to have done the job.[/FONT][/COLOR]

---

