---
title: "Can't Access 192.168.1.1 using my Ubuntu OS"
date: 2018-10-23
forum: General Help
---

### Post by sanjayreddy on 2018-10-23
Hello friends, I Have recently shifted to Ubuntu OS from Window. Then after i have been facing some weird issue with my WiFi connection. So though to Configure it Using 192.168.1.1 which is Default Gateway of mine. I tried Accessing 192.168.1.1 in Ubuntu, But i failed to Connect :confused:.  I am getting a Error message saying "This site Can't be Reached". Actually i new to This OS, Don't no how to Configure my Router settings. Can someone help me Please :(

---

### Post by plucky on 2018-10-23
Have you tried ```
192.168.0.1
``` to access your router?

---

### Post by yancek on 2018-10-23
You should be able to verify what your router IP is with the command:  route -n.  How are you trying to access it.  You might try it in a terminal with the command below if you use firefox, otherwise change to whichever browser you are using.  Might see some error/warning messages that way.

> firefox [http://192.168.1.1](http://192.168.1.1)
 

What is the router manufacturer name?

---

