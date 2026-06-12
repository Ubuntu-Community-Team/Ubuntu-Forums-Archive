---
title: "smb gone after firestarter install"
date: 2007-11-24
forum: General Help
---

### Post by borisattva on 2007-11-24
i installed firestarter and suddenly was no longer able to see my nas in nautilus.
was able to access it via direct IP. removed firestarter and restarted but the problem persists. how can i undo the damage?

---

### Post by borisattva on 2007-11-24
```
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -F
```

i asked the same question on the IRC channel and was told the above code would undo firestarters changes..

i got my smb shares back, but did i open anything else by the above?

also, is it not unusual for an uninstall of an application in linux to not actually remove all changes tha tthe install process has done, like in this case with fire starter?


what can i do, what applciation can i use to track all changes and do a complete restore of the system state with an application removal?

---

