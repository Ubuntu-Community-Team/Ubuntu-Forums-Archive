---
title: "[SOLVED] Keyring Network Encryption Key"
date: 2008-04-01
forum: General Help
---

### Post by jpietari on 2008-04-01
I have an encrypted wireless network at home, which I use Network Manager to set my encryption key.  Every time I start my computer, I have to enter my Keyring password so it can grab the encryption key.  Is there any way of setting this up in Ubuntu 7.10 so I don't have to enter my Keyring password?  If not, will there be a way in Ubuntu 8.04 (PolicyKit)?

I have the same annoyance with Evolution.

---

### Post by blackhole82 on 2008-04-01
I've been searching and searching for an answer to the same problem.  I set up a new computer and I keep getting this too.  I found a post a long time ago that helped me fix it on another computer, but I can't seem to find the same solution or get it working again.

---

### Post by jpietari on 2008-04-02
Check out the info in this post

[http://ubuntuforums.org/showthread.php?t=463621 ]("http://ubuntuforums.org/showthread.php?t=463621")

I haven't tried it yet, but you can get it to work if you disable roaming or turn auto-login off (and modify pam).

---

### Post by jpietari on 2008-04-02
I just turned off roaming, rebooted my machine and wasn't prompted for my Keyring password.

---

