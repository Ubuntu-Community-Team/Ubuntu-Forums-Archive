---
title: "VNC or Remote desktop"
date: 2008-03-19
forum: General Help
---

### Post by n2stc on 2008-03-19
Greetings,  
 
  Has anyone worked out how to access MS/XP remote desktop without having the VNC server running on the target machine?  I'd like to log in to work, but I don't think they would like a VNC server running on their network.

  I look forward to your replies,
S
:D

---

### Post by fedex1993 on 2008-03-19
i dont know about microsoft xp and i dont think this would be the right place to ask asbout MS might want to talk in other os talk

---

### Post by eriqjaffe on 2008-03-19
XP Professional has Terminal Services installed by default, you just have to enable it (and make sure that you have permissions to connect to it).  It could be disabled via Group Policy, however.  That's up to the network admins.

---

### Post by HermanAB on 2008-03-19
Install 'rdesktop' from synaptic then do:
```
$ rdesktop -g 90% ip.add.re.ss
```

Cheers,

Herman

---

### Post by CyberCowboy on 2008-03-19
you could install hamachi [http://www.hamachi.cc]("http://www.hamachi.cc") on both machines and create a network and then use either VNC or RDP without creating a hole in your works firewall, that's  pretty much the only way you're going to get to your work PC, VPN or asking the IT department to open up the firewall to you.

---

