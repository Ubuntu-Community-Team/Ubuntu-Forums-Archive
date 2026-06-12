---
title: "Will this server handle the load?"
date: 2008-05-16
forum: General Help
---

### Post by modulok on 2008-05-16
I am in the process of building a new server for work. The server is a HP DL360 G4 1U server. (dual xeon 3.0ghz, 4GB RAM, and raid1 73gb scsi)

Our network has about 150 users, with 30 being mobile who can work from home (VPN).

[LIST]
[*]content filtering proxy - squid/dansguardian with surftrackr reporting
[*]external ftp - proftp
[*]corporate instant message server - openfire (90 users max)
[*]lightly accessed file server (mostly for ftp files) - samba
[*]web administration - webmin
[*]database - mysql
[*]web server - apache2
[*]firewall - iptables
[*]vpn - openvpn (20 users max simultaneously)
[/LIST]

and possibly in the future:
[LIST]
[*]dns
[*]dhcp
[*]wins
[/LIST]

Will the hardware be enough to support the traffic and load from all of these services?

---

### Post by Monicker on 2008-05-16
Seems like a lot of eggs in one basket.  What will you be using mysql for?  Depending on the amount of data in the tables and the complexity of the queries, that alone can be pretty resource intensive.

---

### Post by Oldsoldier2003 on 2008-05-16
> **Monicker said:**
> **Seems like a lot of eggs in one basket**.  What will you be using mysql for?  Depending on the amount of data in the tables and the complexity of the queries, that alone can be pretty resource intensive.

Its best practice to have one server per service when at all possible. This makes any breach of security less likely to be catastrophic to your organization.

---

### Post by modulok on 2008-05-16
as of me writing this, mysql is just planned for openfire and surftrackr data. I do not see either being that intensive.

Other option I thought of, was breaking up some of the services onto the old server Compaq DL360 G1 1U server (dual xeon 933mhz, 1gb ram, and raid1 18gb scsi).

So that server would look like the following:

[LIST]
[*]DL360 G1
[*]firewall - iptables
[*]vpn - openvpn (20 users max simultaneously)
[*]dns
[*]dhcp
[*]wins
[/LIST]

[LIST]
[*]DL360 G4
[*]content filtering proxy - squid/dansguardian with surftrackr reporting
[*]external ftp - proftp
[*]corporate instant message server - openfire (90 users max)
[*]lightly accessed file server (mostly for ftp files) - samba
[*]web administration - webmin
[*]database - mysql
[*]web server - apache2
[/LIST]

---

### Post by Monicker on 2008-05-16
The latter option seems like a better way to do it.  I agree with Oldsoldier2003 that services should be separated as much as possible.

---

### Post by modulok on 2008-05-16
Yeah OK, that's what I was thinking as well.

The issue with second option, is that the G1 server is the active squid/internet gateway. I would have to figure out everything, and do the install at off-peak hours. The main thing is getting transparent proxy working between the two servers.

I will post elsewhere on that issue when I get there.

---

### Post by modulok on 2008-05-29
[http://ubuntuforums.org/showthread.php?t=810748](http://ubuntuforums.org/showthread.php?t=810748)

This is where I am now, any ideas?

---

### Post by garydauphin on 2009-01-16
Did you ever get your DL360 G1 to work with Ubuntu and the RAID controller?

I am a newbie and have the same hardware and am having lots of issues with the RAID drive.  I would be happy tp pay you $50 to talk me thru the fix.

Basically, I have:
Used the smart software to prep the system volume
Striped the two internal drives
Loaded Ubuntu 8.1 Server on with no problems, and both drives are lighting up.
Upon reboot, I either get a flashing cursor and no boot or
I get: Non-system disk, replace and continue.

Ping me at [email]digitalmus@aol.com[/email] if you can help, please.

---

