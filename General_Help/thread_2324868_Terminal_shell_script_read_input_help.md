---
title: "Terminal shell script read input help"
date: 2016-05-17
forum: General Help
---

### Post by jeff165 on 2016-05-17
basically every time I try to use the read command on any script in my terminal it exits the current operation  here is an example of my script (part of it)

```
#!/bin/bash
adb kill-server
adb start-server
read input 
adb connect 192.168.0.$input
sleep 3
```

here is the out come of the above script 
```

jeff@jeff-X540LA:~$ #!/bin/bash
jeff@jeff-X540LA:~$ adb kill-server
jeff@jeff-X540LA:~$ adb start-server
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
jeff@jeff-X540LA:~$ read input 
45
jeff@jeff-X540LA:~$ 


```
when i press enter after typing 45 it exits 
any help would be appreciated thank you

---

