---
title: "KVM on Ubuntu Server?"
date: 2015-09-28
forum: General Help
---

### Post by mobious2 on 2015-09-28
I recently setup an Ubuntu 14.04 server to act as my media and VPN server. The server is headless and sits in a closet. Is it possible to install VMs to this server and then use them remotely from my Windows desktop? Everything I come access on Google seems to suggest that you are sitting at the VM host machine. 

Thanks for the help!

---

### Post by TheFu on 2015-09-28
Yes. You can do that, but don't expect to watch videos remotely or have any fancy desktops like Unity or KDE.

**x2go** is probably what you want.

---

### Post by mobious2 on 2015-09-28
Thanks. I will check out x2go

---

### Post by TheFu on 2015-09-28
Of course, you can always use ssh (it is a server!) from any network client. 
ssh is the complete network connection/transfer toolkit for Unix systems:
[http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)

For x2go  -- use the PPA and instructions from the official site to install the x2go-server. You'll need to have _some_ GUI installed there too - lxde is light and supported by x2go, so that would be the easiest GUI for someone new. I use a pure-WM environment and openbox.  Setup ssh BEFORE doing x2go.

---

