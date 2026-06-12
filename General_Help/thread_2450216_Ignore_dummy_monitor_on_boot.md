---
title: "Ignore dummy monitor on boot"
date: 2020-09-09
forum: General Help
---

### Post by whonan on 2020-09-09
Hi everyone,
I just recently started using Ubuntu for server machines at work. We install dummy monitors on them since they need to operate headless and we need to access them remotely, and its written to /etc/X11/xorg.conf
Recently we had an IP conflict at a site that caused a few server machines to disconnect from the internet. Since the dummy monitor is set, an onsite tech cannot hook up a monitor and change the IP scheme, and because it's offline I cannot remote into it. 
Is there a way to disable or ignore the dummy monitor setting from the grub when the machine boots up so a tech can see the desktop through a hooked up monitor?

---

### Post by HermanAB on 2020-09-10
Well, you do not need a dummy monitor to run SSH headless.  The SSH server runs on the remote machine (your desktop/laptop).  The SSH client runs on the server in the warehouse.  The client doesn't need to have a screen and the remote server (your desktop/latop) has a screen.  So, once you got your system sorted, remove the dummies, then this won't happen again.

As for fixing the machines, I would plug in a USB-VGA adaptor + screen, boot with any Linux install disc/USB stick, mount the HDD and edit the xorg.conf file.

---

