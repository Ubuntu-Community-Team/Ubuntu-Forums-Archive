---
title: "Remote SSH Connection Stopped Working"
date: 2007-01-18
forum: General Help
---

### Post by rhathar on 2007-01-18
For a while now, I've had a remote SSH connection (openssh-client, openssh-server) running from my computer so I could connect to my computer from work. I've also had a PennMUSH server ([http://www.pennmush.org](http://www.pennmush.org)) running without any problems.

Within the last day or two, my computer seems to have stopped accepting remote connections. When using PuTTY to connect, it times out and never gives the prompt for login username. I have the same problem connecting to the telnet server.

I'm not sure what I did to change anything. The only thing I can think of would be the recent Ubuntu updates, but I don't iknow enough to make a diagnosis.

Any help I could possibly get in this would be very.. helpful :) Thanks.

Edit: Using 'ssh rhathar@localhost' works fine, as does connecting to the PennMUSH server via tf localhost 1375

---

### Post by Jussi Kukkonen on 2007-01-18
> 
Edit: Using 'ssh rhathar@localhost' works fine, as does connecting to the PennMUSH server via tf localhost 1375
You haven't set ssh to accept connections from only certain IPs? If not, then as far as I can see, the only thing that could be wrong with your server is the firewall then. If you haven't touched it. I find it highly improbable that it would have broken.

So, you'll probably have to look further in the network: maybe your router firewall settings have changed or your ISP has started blocking some ports (that's been known to happen).    You could test by changing the ssh port to 80...

---

### Post by rhathar on 2007-01-18
Thank you for responding, and to anyone else that spent time reading this.

Sorry for wasting your time, it turns out I'm just an idiot :P When I restarted my computer, it was reassigned to a new network address (it's not setup to bind itself to one).

Because I have multiple computers on my network, the router is set up to forward various ports to my computer. After being reassigned, it was being forwarded to my friends.

After working on this for several hours, I went to bed only to realize the answer right before I would have fallen asleep :P

Ah, well. At least it's fixed.

---

### Post by dannofoo on 2007-11-06
For anyone else having problems with this, my solution were:  my router were having a bad day with port forwarding, so i deleted all my forward ports, and added them again.

and voila, ssh and alike working again. Wierd, but worked for me.

---

