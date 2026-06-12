---
title: "Internet working slow"
date: 2017-05-13
forum: General Help
---

### Post by heron1337 on 2017-05-13
not actual

---

### Post by wildmanne39 on 2017-05-13
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by heron1337 on 2017-05-13
> **wildmanne39 said:**
> Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.
[http://paste.ubuntu.com/24570653/](http://paste.ubuntu.com/24570653/)

---

### Post by wildmanne39 on 2017-05-14
Let's turn power management off:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

Now set your settings in network manager to match the screenshots.

You need to remove wicd or network manager or they will conflict, I recommend removing wicd.

Reboot

There are some other settings we can change but let's do these first and see how much it helps.

Thanks

---

