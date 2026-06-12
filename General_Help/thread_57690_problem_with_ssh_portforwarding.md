---
title: "problem with ssh portforwarding"
date: 2005-08-17
forum: General Help
---

### Post by msh on 2005-08-17
Hi

I need to forwwrd a port on my local machine to port 25 on my server. I have done it before and remember the command as:

ssh -L 3025:127.0.0.1:25 crunzh,com

but when I login I get the following error message:

bind: Cannot assign requested address
channel_setup_fwd_listener: cannot listen to port: 3025
Could not request local forwarding.

I have tried other ports too instead of 3025 but get the same error. Do anyone have a guess to whats wrong?

My server is running debian stable with OpenSSH_3.8.1p1 Debian-8.sarge.4

---

