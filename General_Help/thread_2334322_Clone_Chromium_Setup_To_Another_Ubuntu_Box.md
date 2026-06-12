---
title: "Clone Chromium Setup To Another Ubuntu Box"
date: 2016-08-18
forum: General Help
---

### Post by wannabegeek2 on 2016-08-18
I use Chromium to browse the web and have all my favorite extensions setup, myriad preferences and passwords saved, etc...

Is there a way to clone this Chromium instance to another Ubuntu box ? Specifically my new work computer.

---

### Post by howefield on 2016-08-18
Your Chromium profile is stored in

```
~/config/chromium
```

Copy that folder to the same location in the new computer.

---

### Post by wannabegeek2 on 2016-08-18
Thanks. I figured as much. 
Will this also capture my extensions..?

---

### Post by howefield on 2016-08-18
> **wannabegeek2 said:**
> Thanks. I figured as much. 
Will this also capture my extensions..?

Yes, the data for your extensions is stored in a sub folder of ~/.config/chromium/

```
~/.config/chromium/Default/Extensions/
```

The other way is to set up a sync account and set it to sync whatever you want.

---

### Post by kansasnoob on 2016-08-18
> **howefield said:**
> Your Chromium profile is stored in

```
~/config/chromium
```

Copy that folder to the same location in the new computer.

+1!

Make sure Chromium is closed when you copy the profile or after pasting it into it's new location it'll tell you it's already running. I've made that mistake with browsers and Thunderbird more times than I can count on my fingers and toes.

---

