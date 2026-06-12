---
title: "azureus and opera permission"
date: 2007-06-12
forum: General Help
---

### Post by Darkjasper on 2007-06-12
Alright I am trying to get opera to automaticly open my torrent files in azureus and it looks good expect when I go to open them it says '/home/jasper/.opera/Az.desktop' Permission denied. So is there any way to give permission to open the launcher.

Thanks for the help.

---

### Post by DagMan on 2007-06-13
I don't have opera installed to see what you mean all that well but maybe just this would do it.  I say that without really understanding what you're trying to do though.
```
sudo chown $USER:$USER home/jasper/.opera/Az.desktop
sudo chmod 777 home/jasper/.opera/Az.desktop
```

---

