---
title: "Database / web / file - server planning."
date: 2008-01-22
forum: General Help
---

### Post by Akula on 2008-01-22
Hello,

I'm currently planning to put up a web/sql/file - server, using Ubuntu server install. In use, the server would be running mainly lampp and bittorrent client and I would like to use it as a LAN file storage as well. This server would be managed from remote connection (putty) on LAN. These are my basic needs from the server.

HW:
I would be grateful if anyone could help me a little bit with hardware on servers. Like what kind of hardware should I have for this kind of server? 

Would 2GB of RAM, and some 'cheap' dual core processor from intel (for example E4300) with in-motherboard integrated video chip be enough or would the processor power be wasted here? I assume I would also need one or two 'fast' HD's and if possible, put them into RAID for faster reading OR backupping in case of HD crash.

SW:
I'm planning to install at least:
*Ubuntu server (lampp included) and
*TorrentFlux as bittorrent client as it has nice web interface.

In software side I would need assistance in server monitoring. As I have decided to go without any kind of graphical window managers and therefore without 'remote desktop sesssion' stuff, I'd pretty much would be dreaming of some kind of a web interface, which would show me server load, uptime, temperatures etc. But as I'm realist I'm just asking for possible existing software to do this. My goal here is that I would not need to open remote connection (for example with putty) and go to server's terminal every time I want to check temperatures and loads.

Any piece of information is useful. Thanks in advance!!

---

### Post by sandr- on 2008-01-23
Are you planning on using this server in a business environment ( for a company ) or for your personal use? Also, how many people will be using your server?

Your 2GB RAM will be just fine, and your processor too ( be sure to install the server edition of ubuntu, so you don't use recources for a graphical environment ! ). The only thing I would invest in is the LAN storage part, a TB is the bare minimum now a days. Should you use RAID, use RAID 1: this provides a mirrored copy of your harddisk ( allows 1 disk to break while still maintaining data ), and a faster seekrate.This is also the cheapest implementation of a RAIDsystem, so you keep your investment low and your cost-per-storage at a minimum. A gigabit-connection to your network will be mandatory. Be aware when you plan on using this server as a mediacenter. HD-movies require a lot of resources.

I'm sorry I am not aware of any webservice that give statistics about all your serverstatistics, maybe someone else can help you with that. Hepthetical: perhaps there is a way in creating a php file that calls out a bash script, where you call out various commands about your server: eg sensors (temperature), uptime, top -head 5, ...

---

### Post by Akula on 2008-01-23
Thanks for the info!

I'm running this more like a personal server. The usage would be quite small as a web server (I run mainly chat, and some php based web 'services'). I'd say about 20-30 connections from outside max at one time. Also my connection (1Mb up / 8Mb down) makes some limitations for the use.

I'm planning to use software raid as hw raid is quite expensive. But I don't know much anything about making raid. I'm going to dig internet a bit in this topic (any links would be welcome).

Thanks for the tip. I could probably code that php script to use in monitoring.

---

