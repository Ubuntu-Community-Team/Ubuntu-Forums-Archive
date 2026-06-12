---
title: "[SOLVED] PAN - No Connection"
date: 2008-02-19
forum: General Help
---

### Post by galeg on 2008-02-19
Installed PAN Newsgroup Reader with the Synaptic Package Manager, then recorded server details the same as utilised with XNews (moving off XP to Ubuntu), but when I try to down load the list of Newsgroups PAN will not connect (No Connection - on bottom left of application window).
Version of PAN installed is 0.129
Do I need to define the PAN port to Firestarter, if so which type of connection do I use in the Firestarter policy, or has somebody also had this problem (possibly something I have not defined in either Firestarter or PAN set up.
Is there depenancies that need to be installed before PAN, that are not automatically installed when PAN installs.
Thanks

---

### Post by torgrot on 2008-02-19
The biggest problem I had with Pan was figuring out to limit the number of connections to three.  My ISP doesn't allow more than three connections and by default Pan is set to four.  Once I lowered it to three all was well.

torgrot

---

### Post by randy78 on 2008-02-19
> **galeg said:**
> Installed PAN Newsgroup Reader with the Synaptic Package Manager, then recorded server details the same as utilised with XNews (moving off XP to Ubuntu), but when I try to down load the list of Newsgroups PAN will not connect (No Connection - on bottom left of application window).
Version of PAN installed is 0.129
Do I need to define the PAN port to Firestarter, if so which type of connection do I use in the Firestarter policy, or has somebody also had this problem (possibly something I have not defined in either Firestarter or PAN set up.
Is there depenancies that need to be installed before PAN, that are not automatically installed when PAN installs.
Thanks

Yes, if  Firestarter is configured to be restrictive by default, then add a rule for NNTP for Firewall Host.

Pan is great!

---

### Post by galeg on 2008-02-19
Thanks all

Problem resolved.

Caused by the expectation that I would need to add User ID and Password for server connection.

When User ID and Password removed, PAN connected to server.

---

