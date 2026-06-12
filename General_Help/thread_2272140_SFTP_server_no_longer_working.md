---
title: "SFTP server no longer working"
date: 2015-04-04
forum: General Help
---

### Post by William_Elliott on 2015-04-04
Hi, I am fairly new to Ubuntu and Linux in general. I am renting a VPS which is running Ubuntu 14.04 i386.
Yesterday I set up an SFTP server using OpenSSH. I was capable of transferring files until I restarted the machine, but now I just can't connect to the SFTP server.
I have tried a few different things but just can't get it working again. For your information, I followed this tutorial when setting up SFTP: [https://www.youtube.com/watch?v=39-NLKPWyTs](https://www.youtube.com/watch?v=39-NLKPWyTs)
Sorry if this comes off as a silly post, but I am still learning and can't seem to fix this problem!

---

### Post by TheFu on 2015-04-05
Does ssh still work?  If not, try **ssh -vvv -p {port} userid@ip-address** to get more debug output.

Did you install fail2ban? You should to prevent brute force attacks.
Did the firewall get enabled? Installing fail2ban should fix that.

Also, be certain to NOT use passwords - setup ssh-keys for authentication.

Not gonna watch some video, sorry.  ssh is one of those things that sorta just works if running, authenticated, and the firewall isn't in the way.

---

