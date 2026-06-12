---
title: "setting up an install for ssh access"
date: 2015-11-07
forum: General Help
---

### Post by matthew_smith2 on 2015-11-07
I will be doing a fresh install on a new build and I will be accessing it ony via ssh.  It will not have a monitor or keyboard attached after the initial install and setup.  It will be located in my home and doing some processing and that's it.

How do I go about setting this up properly?

Thank you.

---

### Post by Lars Noodén on 2015-11-07
If you are using UFW, the packet filter / firewall interface, then adjust that to allow port 22 in.  I usually use rate limiting there, too.  

The package providing SSH access is *openssh-server*.  Once you have that installed in its basic configuration you have SSH access.  It's a good idea to turn off root login there, the newer versions (>= 7.0) of OpenSSH default to allowing only keys for root, but the older versions have to be configure so.  

Next, you'll want to set up key access using big RSA keys or Ed25519 keys.  Once the keys are working, especially if the machine is going to have a port facing the Internet, you'll want to turn off password authentication for the SSH server.  

Be sure to at least skim the manual pages for sshd_config and sshd both now before you start and after you've made some progress.  They and the other OpenSSH manual pages are very well written.  Ubuntu has some guides here, but the manual pages are the ultimate documentation about what can be done and how.  :
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

The forum is available too of course.

---

