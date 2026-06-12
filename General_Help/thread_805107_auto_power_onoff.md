---
title: "auto power on/off"
date: 2008-05-23
forum: General Help
---

### Post by Dashman403 on 2008-05-23
Is there any program or chip that would automatically turn a computer on and off at certain times?

---

### Post by barnex on 2008-05-23
Powering off your machine is possible with the command 'halt', e.g.: ```
echo halt | at 23:48
```
This will shut your machine down at the specified time. You will have to run this as root.

---

### Post by retrow on 2008-05-23
w.r.t. starting your machine at a certain time - You can do that in your BIOS setup. Usually there is an option called Power Management in your BIOS setup.

---

### Post by nick_h on 2008-05-23
You could also use the shutdown command:
```
sudo shutdown -h 12:34
```

---

