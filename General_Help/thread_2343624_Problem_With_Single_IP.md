---
title: "Problem With Single IP"
date: 2016-11-17
forum: General Help
---

### Post by shane_faulkinbury2 on 2016-11-17
I've been checking for IPi's trying to or already logged onto my computer using the netstat -ntu | awk '/ESTABLISHED/{print $5;}' command .  Every single day I find an IP from Canonical Ltd and the IP is 91.189.94.25.  See the attached .png.  Anyway I have the IP blocked using UFW and IPTABLES, but I'm wondering is it really Canonical or are they some kind of ISP in England?  I can't do anything about it because I'm an American citizen and I doubt Great    	 	 	 	   	 	 	 	Britain would do anything about them.  I also should tell you I'm not logged into anything Ubuntu related when I catch the IP.

---

### Post by TheFu on 2016-11-17
Does the system check for updates daily?

BTW, I can't read that img. Please copy/paste text output from shell cmds.

---

### Post by shane_faulkinbury2 on 2016-11-17
The img is just a screen shot from whatsmyipaddress.com showing that IP is from Canonical.  It's not from updating because the IP still shows for an hour after I disconnect my wifi and unplug my wifi adapter.

---

### Post by untrustytahr on 2016-11-17
There's a lot of housekeeping that goes on in the background in addition to software updates.  NTP for time and geoip for timezone etc.

---

### Post by shane_faulkinbury2 on 2016-11-18
Highly doubtful.  Today I've been logged in for 5 hours and now they're trying to access through ports 80 and 443!

---

### Post by TheFu on 2016-11-18
That netstat command shows output connections.  They aren't likely to be trying to access your system. It is the other way around. Your system is accessing their server.  If you have the port, use lsof to trace back to the process. Then you'll know. You'll want to not filter the other columns to see the local port used.

For example: 173.194.219.16:993 shows up on my desktop, but none of my servers.  That is an IMAPS connection to gmail. Local port is 46006/tcp which leads to the thunderbird process (and lots of thunderbird libraries).  Makes perfect sense.

In short, it is your system asking, not them attacking.

---

### Post by shane_faulkinbury2 on 2016-11-18
Netstat doesn't just show outgoing connections.  Look at the attachment.  I have nothing to do with Verizon nor any Verizon page open!  So why would they be trying to access my computer?

---

### Post by shane_faulkinbury2 on 2016-11-24
Hmm, I guess nobody wants to comment on Ubuntu trying to hack me!

---

### Post by lisati on 2016-11-24
> **shane_faulkinbury2 said:**
> Netstat doesn't just show outgoing connections.  Look at the attachment.  I have nothing to do with Verizon nor any Verizon page open!  So why would they be trying to access my computer?

It's probably not Verizon who's doing it per se, but more likely a customer with a compromised machine. You might want to look into making adjustments to the firewall settings on your router and computer.

---

