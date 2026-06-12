---
title: "Start Java program with new screen session at boot"
date: 2018-10-30
forum: General Help
---

### Post by arya6000 on 2018-10-30
I am trying to run a java program inside a screen session at boot, I am using the following cron, the screen session does get created after boot, but the program is not running inside it.


```
@reboot /usr/bin/screen -dmS myprogram && /usr/bin/java -jar /home/root/myprogram/MyProgram-0.0.1-SNAPSHOT.jar
```

Any idea what needs to be done to make the Java program start inside the new screen session?

---

### Post by spjackson on 2018-10-31
I don't use screen, but probably removing '&&' should do it. What your command means as it stands is to run screen then only once screen has exited with a status of 0, run java separately.

---

### Post by arya6000 on 2018-10-31
> **spjackson said:**
> I don't use screen, but probably removing '&&' should do it. What your command means as it stands is to run screen then only once screen has exited with a status of 0, run java separately.

When I remove the "&&" then so screen gets created at boot

---

