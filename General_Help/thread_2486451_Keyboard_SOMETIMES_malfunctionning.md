---
title: "Keyboard SOMETIMES malfunctionning"
date: 2023-05-01
forum: General Help
---

### Post by alreve on 2023-05-01
It started with the space bar : no effect when I pressed on it. 
I plugged in an external keyboard (via usb) and this functioned perfectly. 
I thought some little piece of dirt had got under the space key. 

Next reboot : all keys malfunctioned. What seemed like totally random characters appeared. External keyboard still fine. 

I typed : 

```
sudo dpkg-reconfigure keyboard-configuration
```

and rebooted. Original keyboard functioned fine. I thought I had fixed it.

Next reboot : the space key malfunctioned again. I retyped the above command and rebooted : no effect. 

Could someone please explain? Of course I would also like to know the (permanent!) fix, but I would also really like to understand how such behaviour is possible.

---

### Post by guiverc on 2023-05-01
You seem to be describing hardware issues (*with your keyboard*).

I usually use `xev` to explore keyboard/mouse issues.

---

