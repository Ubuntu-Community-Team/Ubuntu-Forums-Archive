---
title: "SSH tunnel + Proxy for everythign"
date: 2008-03-16
forum: General Help
---

### Post by Darth_tater on 2008-03-16
Help!

my request is different from all the other ones that can be seen on theese forums, as i need a complete proxy.  let me explain. 


occasionally i find myself in a place where i can not trust the internet connection and would like to securely to my server here at home.  unlike everybody else, i need more than HTTP proxy abilities.  i need my IM clients and IRC clients to work as well as some other applications that do not use HTTP ports.

i need to create a global proxy on my laptop ( a windows xp pro machine) that will SSH all network requests to my server here.

[laptop] <---(ssh tunnel)---> [my home server] <---(my normal dsl line)--->  [internet]


how can i accomplish this?  i need to configure windows to put ALL internet traffic into a single SSH tunnel and i how do i configure the server on the back end?  


-- thanks in advance fo any and all help you can provide me!

---

### Post by whoop on 2008-03-16
Could you not just use vnc via ssh tunneling ?

---

### Post by Darth_tater on 2008-03-16
no, not really.

the server is CLI environment only.

and VNC would KILL the bandwidth of practically any location i happened to be at.

good suggestion, though.

---

### Post by whoop on 2008-03-26
Ok, then what about X11 forwarding through ssh? Wouldn't this require less bandwidth?

---

### Post by Darth_tater on 2008-03-26
> **whoop said:**
> Ok, then what about X11 forwarding through ssh?


the server is CLI only, so SSH is easiest for when i need direct access to it. 

even if i had a GUI, X11 forwarding through SSH would consume just as much bandwidth as vnc and be only marginally faster.

my HTTP tunnel works for now and most of my applications can be configured to use a SOCKS proxy (i just have to set them to 127.0.0.1 and my magic port after i get PuTTY launched and connected)

i guess what i really wanted is a VPN w/o all the hassle.  oh well, what i have now works and my DDWRT router supports direct VPN so i might be able to mess around w/ that this weekend.


thanks for your help, though

---

