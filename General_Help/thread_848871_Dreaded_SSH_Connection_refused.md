---
title: "Dreaded SSH Connection refused"
date: 2008-07-03
forum: General Help
---

### Post by Cata1yst on 2008-07-03
hey guys,

been working on my server a bit and have been following this guide
[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/6](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/6)
its been going smoothly until i get to the remote management (which hates me)...the client gave me a little trouble installing and configing, but i eventually got it all.
Now when i try to connect to putty following that guide down to the period, it gives me the dreaded "Connection Refused" error when i connect with 192.168.0.2 (local ip of my server)

If i go to the server and do ssh localhost, she works fine so im guessing that my ssh is doing it correctly.
I have retraced my steps starting again with the configuring of the remote management but its still a no go, and like i said i have been following that guide to the period, only to venture off to do "makedir ~/.vnc" or else vncpasswd wouldnt change for x11vnc

i even went to the extent of following this [http://www.thelinuxvault.net/wiki/X11vnc](http://www.thelinuxvault.net/wiki/X11vnc)
any ideas?

oh and im connecting using ultravnc on windows (i know, i know, but im a gamer first and thats my only option pretty much)

---

### Post by AnarkistNZ on 2008-07-03
First of all, are you trying to SSH or use VNC?

There's a difference between the two. SSH being remote command line access, and VNC being remote desktop.

Also, as an aside.. If you're inside the LAN, and you're not able to connect to your box on SSH port 22, yet you're able to connect to it from localhost then it would suggest there is a firewall or a configuration issue blocking these requests.

---

### Post by Cata1yst on 2008-07-04
well im trying to tunnel through SSH with VNC for security..but i think i can live with just VNC working if theres a guide that anyone could link me to? i tried search...wasnt too friendly

is there anything i should check for the server side box? firewalls or anything? and my router has a NAT firewall...should i disable that?


oliver

---

### Post by Cata1yst on 2008-07-04
bump?

---

### Post by krunge on 2008-07-05
> **Cata1yst said:**
> 
is there anything i should check for the server side box? firewalls or anything? and my router has a NAT firewall...should i disable that?

Did you check all of these yet?  What are your findings?

---

