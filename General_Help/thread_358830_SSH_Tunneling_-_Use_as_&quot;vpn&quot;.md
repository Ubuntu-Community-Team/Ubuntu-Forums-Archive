---
title: "SSH Tunneling - Use as &quot;vpn&quot;?"
date: 2007-02-11
forum: General Help
---

### Post by russx2 on 2007-02-11
Hi,

I'm not sure how exactly to phrase this question so I'll start with what I'm trying to achieve.

I have a "home" computer (6.06) that I can connect to remotely. There are other computers, on the same local network as the one I can connect to externally. 

Now I can make an SSH tunnel (ssh -D 9999 user@host) which is great. But I'd also like to be able to talk to the other computers (via the one I can connect to). Is there any way of mapping that network onto the remote PC?

e.g. I create the tunnel, then all requests to 10.0.0.X go to the respective internal machine?

I think I've managed to get my question accross - any ideas would be greatly appreciated!

Thanks,

Russ

---

### Post by schilcha on 2007-02-11
Have you tried using the ssh's -w switch? I've tried it once, but failed because of insufficient priveliges on the remote machine -- to debug your tunnel add the parameter -v to your ssh-command, so you'll see which steps failed and which succeeded.

However, it sounds promising: as I understood the man-page, it persuades ssh to create tun-devices on the client an the server. On both machines, you can set up routes accordingly, to route traffic through the ssh-tunnel as needed. 

Sorry, but I can't supply you any practical experiences on this, but it might be worth a try.

Good luck!

---

