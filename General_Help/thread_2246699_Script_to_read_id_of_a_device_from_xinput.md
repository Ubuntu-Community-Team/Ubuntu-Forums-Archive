---
title: "Script to read id of a device from xinput"
date: 2014-10-02
forum: General Help
---

### Post by Digital Ninja on 2014-10-02
I currently run a script on login, that lowers my mouse sensitivity, because the normal lowest sensitivity is not low enough. 

```
xinput --set-prop 10 "Device Accel Constant Deceleration" 4
```

But since the id of my mouse changes on almost every login, updating the id in the script is useless and I end up having to run the command manually almost every time. How would the script have to be updated to read the id of the "Genius Optical Mouse" device from the `xinput` output, and then run the previous line for its id?

---

### Post by Vaphell on 2014-10-02
```
id=$( xinput list --short "Genius Optical Mouse" | grep -Po '(?<=id=)[0-9]+' )
xinput --set-prop "$id" "Device Accel Constant Deceleration" 4
```
or whatever the xinput --set prop syntax is

---

### Post by Digital Ninja on 2014-10-03
It seems to work great, thank you so much!

---

