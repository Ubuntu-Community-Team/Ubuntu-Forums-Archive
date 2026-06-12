---
title: "NAT error in Azureus"
date: 2006-11-07
forum: General Help
---

### Post by EmperorSquirrels on 2006-11-07
After a long and grueling experience I finally got Azureus working. But there's still one minor problem - my speed is being dwarfed by a firewall or a NAT error. My connection does through, I know that. The port test worked fine. Does Edgy have a firewall I don't know about?

Any help would be appreciated. Thanks.

---

### Post by eran- on 2006-11-07
You'll have to activate port forwarding from your router. NAT stands for Network Address Translation, which is explained with more details in [here]("http://www.azureuswiki.com/index.php/PortForwarding"). :)

---

### Post by EmperorSquirrels on 2006-11-07
Oh, I already forwarded the ports. Before, it wouldn't even connect. After I forwarded them they connected, but my download speed is TINY. Not even more than 5kbps.

I set it to port 55680.

---

### Post by EmperorSquirrels on 2006-11-07
Okay nevermind, I guess letting it "simmer" a bit turned that "Firewalled" button off. But now the problem remains - my upload speed is at a constant 0kbps. Now, for most people wouldn't consider that a problem, but I'm one to give back to whatever community I'm downloading from. So it's a big deal to me.
Any ideas?

---

### Post by Orosius on 2006-12-17
I had a similar problem. After forwarding the ports in my router, I installed firestarter. In this program I made a policy to allow the services on these ports for anyone (you can also open these ports using the 'iptables'-command, but that was too difficult for me ;) ). 
I thought my problem was fixed, but my speeds were still very low. I eventually found something in another forum. I don't know exactly what it does, but it boosted my download speed from 5 kbps to 50 kbps: 

In /proc/sys/net/ipv4/ip_forward, I replaced the 0 with a 1. Then, restarted networking by doing "sudo /etc/init.d/networking restart".

---

### Post by Orosius on 2006-12-23
I noticed that this flag is set back to 0 the next time you start your computer. I think the following makes it last: 
in /etc/sysctl.conf you have to uncomment the line that says: "net.ipv4.conf.default.forwarding=1"

---

