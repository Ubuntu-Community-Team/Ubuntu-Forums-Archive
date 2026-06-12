---
title: "Ubuntu 17.10 fails to boot.  This is the only error message"
date: 2018-03-23
forum: General Help
---

### Post by U2XS on 2018-03-23
[SIZE=3]**Edit: ** It was a GRUB2 issue.  Following Linode's tutorial on how to enter rescue mode & change root, I was able to access the grub.cfg file & swap out the incorrect UUID.  [https://www.linode.com/docs/troubleshooting/rescue-and-rebuild/#change-root](https://www.linode.com/docs/troubleshooting/rescue-and-rebuild/#change-root)
[/SIZE]



I'm running Ubuntu 17.10 on Linode and today it failed to boot.  I am able to use the graphical user interface to see what the OS is doing and this screenshot is the only error it gives.  After that, it goes to a blank screen.  I cannot SSH into it & it does not respond to ping.  I do have access to "rescue mode" (Based on [Finnix recovery distribution]("https://www.finnix.org")), which does let me type commands.  

My theory is that I ran an update over the course of the last month and never rebooted the OS.  So when it finally did reboot, it failed.  If that's the case, then potentially the issue is GRUB2.  However any attempt to run "grub-install" results in the error "command not found".  

Thoughts?

[IMG]https://i.imgur.com/ycVGlbg.png[/IMG]

---

