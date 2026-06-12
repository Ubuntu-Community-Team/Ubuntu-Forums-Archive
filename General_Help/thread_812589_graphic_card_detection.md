---
title: "graphic card detection"
date: 2008-05-30
forum: General Help
---

### Post by anksi4u on 2008-05-30
i have installed hardy recently and have found that althought in the restricted hardware section the nvidia-new tab is enabled but it says that it is not in use.
So i cant increase my resolution from 800x600 what should i do?

---

### Post by jean noel on 2008-05-30
> **anksi4u said:**
> i have installed hardy recently and have found that althought in the restricted hardware section the nvidia-new tab is enabled but it says that it is not in use.
So i cant increase my resolution from 800x600 what should i do?

i had the same problem when i installed 8.04. i just disabled the driver, restarted the computer, and re-enabled the  ati driver. Worked fine.
:)

---

### Post by anksi4u on 2008-05-30
> **jean noel said:**
> i had the same problem when i installed 8.04. i just disabled the driver, restarted the computer, and re-enabled the  ati driver. Worked fine.
:)

well but its not working for me it keeps on saying that the driver is not in use even though the option is checked

---

### Post by PmDematagoda on 2008-05-30
> **anksi4u said:**
> well but its not working for me it keeps on saying that the driver is not in use even though the option is checked

Kill the X-Server with:-
```
sudo /etc/init.d/gdm stop
```
run nvidia-xconfig:-
```
sudo nvidia-xconfig
```
start the X-Server:-
```
sudo /etc/init.d/gdm start
```

See if that fixes the issue.

---

### Post by anksi4u on 2008-05-30
> **PmDematagoda said:**
> Kill the X-Server with:-
```
sudo /etc/init.d/gdm stop
```
run nvidia-xconfig:-
```
sudo nvidia-xconfig
```
start the X-Server:-
```
sudo /etc/init.d/gdm start
```

See if that fixes the issue.

tried it out but it says that command not found..
the nvidia command doesn't seem to exist

---

### Post by PmDematagoda on 2008-05-30
Then try:-
```
sudo nvidia-settings --config enable
```

---

