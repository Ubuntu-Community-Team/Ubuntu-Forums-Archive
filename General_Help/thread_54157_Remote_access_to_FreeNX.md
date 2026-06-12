---
title: "Remote access to FreeNX"
date: 2005-08-03
forum: General Help
---

### Post by neilbain on 2005-08-03
Hi

I have FreeNX running on the latest Kubuntu distro.  All works perfectly when attaching from an XP laptop running NoMachine nxproxy version 1.5.0 over my LAN.  SSH is not enabled and FreeNX was set up with the --setup-nomachine-key modifier. (I know, I know... not very secure but I'll sort that out when I solve the problem below).

My problem occurs when I try to connect from outside of my network.  NXproxy finds the server, authenticates sucessfully but then fails when "negotiating link parameters".  NXproxy also reports "Aborting the procedure due to signal '15', 'SIGTERM'"

I am  firewalled via a Netgear WRT511G wireless router.  I have port forwarding for port 22 to the server set.

Any solutions?? or any additional information required of me to help get to a solution?   

I am a newbie so clear instruction would be very much appreciated!!  :roll: 

Thanks

Neil ](*,)

---

### Post by neilbain on 2005-08-05
:-# What? Does NOBODY have any suggestions (sensible or otherwise!)

---

### Post by Maxplayer14 on 2005-08-05
I use SSH and mine works like a charm.  I actually use my FTP port 20 to get in.  Wish I could be more help.

---

### Post by neilbain on 2005-08-08
SOLVED

I also needed port 5000 opened and forwarded to the server.  All working now. :-P 

Neil

---

