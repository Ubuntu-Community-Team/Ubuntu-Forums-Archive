---
title: "How to turn off IPtables"
date: 2005-10-24
forum: General Help
---

### Post by stack445 on 2005-10-24
Since the upgrade to breezy, azureus does not download anymore. I know that my cable router is correct, beacause in windows it works very well. I've look around, and did find some stuff but noting work. 

So it must be that ubuntu has a firewall on of some sort right ? I used firestarter to actualy stop the firewall but it had no effect. Also, is there a other bittorent client that is not a ressource hog like azureus. It seem that the java thing is taking a lot of cpu... 

thanks

---

### Post by bionnaki on 2005-10-24
completely uninstall firestarter & reboot.

---

### Post by evil-boweevil on 2005-10-24
I'm having the same problem, I don't think it's a firewall thing because I've never installed a firewall or had one running.  Other P2P programs work well.

---

### Post by Kyral on 2005-10-24
IPTables is actually "blank" until another program (like Firestarter) acts on them. To list the current rules

```
sudo iptables -L -v
```

If its blank (except for headers like CHAIN INPUT) then iptables isn't doing a damn thing.

Oh BTW, BitTornado works nicely

---

