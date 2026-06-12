---
title: "&lt;help&gt; want to build home server with hardy heron"
date: 2008-05-20
forum: General Help
---

### Post by anak_design on 2008-05-20
Dear All,

I'm looking for some information before I started this project of mine.

I want to create a home server for music, videos, web and work (small business) server. I decided to choose linux since it's free, and known for its stability. So, here's my project:

**PURPOSE:**
1. File Server (music & videos & photos)
2. P2P Client (download torrents)
3. Light daily use (browsing net, getting familiar with linux)
4. Web Server (future plan)

**HARDWARE:**
1. *Intel / AMD (?) - Heard AMD is cheaper with decent performance, true?*
2. 1 - 2GB RAM
3. 500 - 1TB SATA HDD
4. *Gigabit LAN / Wireless 801.2n - Considering I need a fast network for a server(?)*
5. DVD-RW

Please help regarding the hardware I had to choose. I'm thinking of using Gigabyte's motherboard since it usually has quite some features. But when it come to processor, and network, I'm kinda confused, whether it's better to have gigabit cable connection or wireless-n.

Do let me know if you have a similar experience.

Thanks.

---

### Post by compgeek83 on 2008-05-20
> **anak_design said:**
> Dear All,

I'm looking for some information before I started this project of mine.

I want to create a home server for music, videos, web and work (small business) server. I decided to choose linux since it's free, and known for its stability. So, here's my project:

**PURPOSE:**
1. File Server (music & videos & photos)
2. P2P Client (download torrents)
3. Light daily use (browsing net, getting familiar with linux)
4. Web Server (future plan)

**HARDWARE:**
1. *Intel / AMD (?) - Heard AMD is cheaper with decent performance, true?*
2. 1 - 2GB RAM
3. 500 - 1TB SATA HDD
4. *Gigabit LAN / Wireless 801.2n - Considering I need a fast network for a server(?)*
5. DVD-RW

Please help regarding the hardware I had to choose. I'm thinking of using Gigabyte's motherboard since it usually has quite some features. But when it come to processor, and network, I'm kinda confused, whether it's better to have gigabit cable connection or wireless-n.

Do let me know if you have a similar experience.

Thanks.

You have the right range for your hardware, I'm an AMD person, have been for a long time, and others may argue but I think you get more performance for you dollar.  2GB of ram would be plenty for starters, make sure it's 2 1GB sticks or 1 2GB Stick of DDR2 800mhz, this allows you expandability, although some boards out now do have 4 ram slots.

I'm wholly against wireless for a server, it's great for sitting on the couch on your laptop but you want the server to work 99.9% of the time...  I've picked up businesses (I run a repair shop) that have been set up by others with wireless everything and they have nothing but problems, have to reboot and re-connect to the wireless network atleast once a day on each pc (and that's one without a server).  I switch them to 10/00 networking (1 even to gigabit due to a server) and they actually like to come to work now.

as far as the linux distro, I would pick xubuntu.  I'm new to ubuntu myself, have been running it on my main desktop for a few weeks now.  I'm going to experiment with updating my server to xubuntu (suppossedly faster than ubuntu) my only issue is getting a linux-based dvr software to monitor my security cameras, I'm looking at zoneminder at the moment.

another distro I've read about is mythbuntu for home media servers, you might want to look into that.

---

### Post by Thirtysixway on 2008-05-20
If you're lookig at keeping a GUI on it, I would, too, suggest Xubuntu for the lightweight desktop.  Otherwise, you can use Ubuntu Server edition.  Here are some things you could use:

Webmin - Remote management of all the services/server
Samba - File sharing between pretty much all operating systems over the network
Torrentflux - Torrent client with web interface
Browser - Just use firefox, although I wouldn't recommend browing the web on your server.
Web server - Get apache with php5, mysql, phpmyadmin

These are just suggestions, geared more toward the type of server you would put in your closet, not on your desk.  You may also want to setup remote desktop or ssh.

---

### Post by anak_design on 2008-05-21
**@compgeek83**

I'm not really following what has been happening to AMD. Which processor/model should I use that would be sufficient for my build? If you could recommend a few that would be great.

As for the network, yea, I decide to just rely on cable still. I guess N based network is not worth it that much yet?

Xubuntu huh? I'll look into it.

**@thirtysixway**

Thanks for the apps suggestions.

---

