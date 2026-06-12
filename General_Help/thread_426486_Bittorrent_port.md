---
title: "Bittorrent port?"
date: 2007-04-28
forum: General Help
---

### Post by midlandman on 2007-04-28
Hi.
Can someone tell me how to see what port the bitttorent that comes with Feisty uses?
I use a router and I'd like to see if I can get a bit more speed by using a different port.
Thanks.

---

### Post by fwojciec on 2007-04-28
6881 by default

you can change it and configure few other settings using Gnome Configuration Editor (gconf-edit - run it as root if you don't have the menu entry for it).  Once in Configuration Editor navigate to apps/gnome-btdownload/settings.

---

### Post by Slim Odds on 2007-04-28
> **midlandman said:**
> Hi.
Can someone tell me how to see what port the bitttorent that comes with Feisty uses?
I use a router and I'd like to see if I can get a bit more speed by using a different port.
Thanks.

Why to you think that a different port would have more speed?

That makes no sense.

---

### Post by aldenhg on 2007-04-28
You're not goig to speed up torrents by changing your port unless your ISP is doing some bandwidth shaping on the port that you're using now. If you want more speed, I'd reccomend that you check you firewall/router setting to make sure that the port you're on right now is being forwarded.

---

### Post by midlandman on 2007-04-28
Maybe it doesn't make sense to you, Slim, but when I was using ABC with XP I was getting speeds like 25-30k, then after changing the port I was getting 100-200k's.
I also changed the port for Azureus and it's moving faster than the default client in Feisty.
Actually, it doesn't make a lot of sense to me either. But I did get results from changing ports in my router.
And thank's FW, I'll give it a try.

---

### Post by noerrorsfound on 2007-04-28
> **Slim Odds said:**
> Why to you think that a different port would have more speed?

That makes no sense.
A lot of ISPs block default BitTorrent ports or interfere with them in some other way. So if your ISP does that then yes, you will gain speed by switching ports.

---

### Post by Slim Odds on 2007-04-28
> **noerrorsfound said:**
> A lot of ISPs block default BitTorrent ports or interfere with them in some other way. So if your ISP does that then yes, you will gain speed by switching ports.

I'll bet that if your ISP is "smart" enough to adopt speed shaping, then they can figure out that you've changed ports.

---

### Post by midlandman on 2007-04-28
I never had any problem after changing the ports. Maybe some isp's are more aggresive when it comes to this sort of thing?

---

### Post by hencethus on 2007-05-01
I definitely got much better download speeds after changing ports.

I've heard that many ISPs block port 6881.

Now I'm using 10000 through 10100 with no problems.

Also, the command to open the Configuration Editor is **gconf-editor**.

---

### Post by mozetti on 2007-05-01
> **Slim Odds said:**
> I'll bet that if your ISP is "smart" enough to adopt speed shaping, then they can figure out that you've changed ports.

Sure, if they're sniffing traffic and shaping it that way. But, if they're just restricting the default torrent ports (which some are doing) then changing a port increases your speeds. If ISPs are gonna do any throttling/shapping they won't do by dynamically adjust port speeds on a per user basis, they'll just sniff the content for torrent traffic and do it that way. That's why people use torrent clients that support encryption, then they can't tell what your traffic is by sniffing.

Sounds like the original-poster's ISP uses the port-based solution, so changing ports should work.

---

### Post by jsilvanus on 2008-04-02
Thank you for those, who posted in this thread. I got the info I needed and changed the ports to 60111-60122. I'm using this high ports because behind the router we have multiple users and most are not as geeky as me. So, I added myself a cloud of open ports high up, I don't think others are using them.

---

