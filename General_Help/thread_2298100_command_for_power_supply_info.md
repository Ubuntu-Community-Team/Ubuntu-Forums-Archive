---
title: "command for power supply info"
date: 2015-10-09
forum: General Help
---

### Post by bobmac on 2015-10-09
Folks,

Is there a command that I can use to get my power supply data?.

Regards,

Bob

---

### Post by Yellow Pasque on 2015-10-09
There is no command to query the model number, wattage rating, etc. if that is what you're asking for.

You may be able to check the voltage levels with sensors if your motherboard supports it. They're not always accurate and correctly labeled though:
```
sudo sensors-detect     #you only need to run this command once and not every time you want to see sensors
sensors
```

---

