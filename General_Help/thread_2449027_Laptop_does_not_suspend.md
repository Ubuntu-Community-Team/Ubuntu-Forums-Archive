---
title: "Laptop does not suspend"
date: 2020-08-18
forum: General Help
---

### Post by mustermark on 2020-08-18
Hi,
I'm running Ubuntu 16.04 on a Dell xps13. Everything was running fine until a couple of days ago, when the laptop stop suspending when I closed the lid (as it used to). I checked that the laptop doesn0t suspend from the command line either (using ```
 systemctl suspend 
```). In all cases, when the laptop is supposed to suspend it switches off. The configuration in the system settings is fine, and I've tried without success uncommenting in /etc/systemd/logind.conf the lines 
```

HandleSuspendKey=suspend
HandleHibernateKey=suspend
HandleLidSwitch=suspend
HandleLidSwitchDocked=suspend

```

Does anyone have any idea about what may be causing the problem?
Cheers!
Pablo

---

