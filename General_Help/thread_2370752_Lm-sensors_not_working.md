---
title: "Lm-sensors not working"
date: 2017-09-06
forum: General Help
---

### Post by raleigh3 on 2017-09-06
I can not get sensors working correctly.

It does not create a sensors.conf despite using sensors-detect.

I am using it on an HP G60 laptop.

---

### Post by gifford on 2017-09-06
After you ran sensors-detect, did it list modules that need to be loaded? If so, did you answer yes to all of the yes/no questions?

---

### Post by raleigh3 on 2017-09-06
I found this. I think 107 degrees F is a reasonable temp for a laptop.
 
```
andy@7:~$ acpi -t -f
Thermal 0: ok, 107.6 degrees F
Thermal 1: ok, 107.6 degrees F
```

---

