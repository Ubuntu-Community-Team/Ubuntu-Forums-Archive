---
title: "ubuntu doesn't work properly at all - please help"
date: 2007-01-24
forum: General Help
---

### Post by frogger fodder on 2007-01-24
hey there

i am new to ubuntu and have just recently installed edgy... there are a few problems:

everytime i log into ubuntu the bug buddy comes up because something has crashed.
everytime i try to access "home folder" or "computer" it crashes and bug buddy comes up.
everytime i try to run office it crahses and bug buddy comes up
mozilla can access the internet (after disabling IPv6) but i cant sign in with Gain as it just doesn't connect properly.
also when i scroll up and down on web pages it is very jerky and sluggish; taking like a second to scroll one click up/down. (if that makes sense)

if any one could help me out it would be greatly appreciated. cheers

---

### Post by taurus on 2007-01-24
Are you using Dapper or Edgy?  Boot into recovery mode from GRUB menu and paste the outputs of these two commands here.

```
df -h
fdisk -l
```

And for firefox, sounds to me like you need to install a driver for your graphic card.

---

