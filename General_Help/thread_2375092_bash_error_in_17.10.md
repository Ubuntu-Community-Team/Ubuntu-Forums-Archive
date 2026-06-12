---
title: "bash error in 17.10"
date: 2017-10-21
forum: General Help
---

### Post by pfd272 on 2017-10-21
When I open a terminal I get the following error message. Terminal still works fine.

 ```
cat: /sys/class/hwmon/hwmon0/temp1_input: Operation not supported
(standard_in) 1: syntax error
```

---

### Post by drs305 on 2017-10-21
It is most likely a problem with a temperature monitoring setting in a.conf file (such as /etc/sensors.conf) or something similar. You can probably see the error by running "sensors-detect" as root (select YES).  

In my system, interestingly, I have a sensor file in my GIMP snap at /snap/gimp/25/etc/sensors3.conf

---

