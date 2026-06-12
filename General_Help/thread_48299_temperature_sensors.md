---
title: "temperature sensors"
date: 2005-07-11
forum: General Help
---

### Post by DarkManX4lf on 2005-07-11
i didnt know where topost this, since it deals with an application, and hardware so i guess i'll post here, since i already posted 4 active topics in the hardware section  :grin: 

so i want to know how to check my cpu temp and other temps inside my case, so i installed lm-sensors, and in the terminal i typed sensors to start it up and here is what it says:

root@ubuntu:~ # sensors
No sensors found!


hmm how do i get it to work? is there a config somewhere ?

---

### Post by jasmuz on 2005-07-11
[QUOTE=DarkManX4lf]i didnt know where topost this, since it deals with an application, and hardware so i guess i'll post here, since i already posted 4 active topics in the hardware section  :grin: 

so i want to know how to check my cpu temp and other temps inside my case, so i installed lm-sensors, and in the terminal i typed sensors to start it up and here is what it says:

root@ubuntu:~ # sensors
No sensors found!


hmm how do i get it to work? is there a config somewhere ?[/QUOTE]
 Hello there :)
You must first configure your sensor reading like so, sudo sensors-detect
Configure them. and afterwards you can run sensors.

Ps: you can use gkrellm when your done to have a nice frontend to all the system checks.

---

