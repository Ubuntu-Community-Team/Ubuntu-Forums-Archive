---
title: "Whats the command to reboot the thernet connection?"
date: 2006-07-13
forum: General Help
---

### Post by slimdog360 on 2006-07-13
I tried to google it and searched the forums but I dont think I was able to word it correctly. 
 I had to change some modem settings and when the modem its self rebooted I was left with no internet. 
 The first time I just rebooted the computer and the second time I rebooted it through the network settings graphically. 
 But that is all very slow so I want a command that I can type into the terminal which will restart the ethernet.
Thanks

---

### Post by scxtt on 2006-07-13
**ifdown eth0** will take eth0 down, then **ifup eth0** will bring it back up ... you might have to sudo that ...

---

### Post by mcduck on 2006-07-13
'sudo /etc/init.d/networking restart'

---

