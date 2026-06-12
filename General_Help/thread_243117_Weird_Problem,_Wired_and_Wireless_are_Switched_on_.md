---
title: "Weird Problem, Wired and Wireless are Switched on Ubuntu Dapper on Dell 600m Laptop"
date: 2006-08-24
forum: General Help
---

### Post by amsgwp on 2006-08-24
I've installed ubuntu dapper drake on this laptop before with no problems(installed breezy and upgraded to dapper).  Well now that dapper drake was officially released it was my first time installing dapper drake from the CD using the graphical installer.  I'm not sure what happened but I just figured out that my wired and wireless connections are switched.

I have eth0(wired according to config page) disabled and wireless eth1 enabled in the settings.  Well I couldn't get it to connect so I said wtf and plugged in the ethernet...**my wireless connection went to 100% signal!**  Wired connection still disabled.  What happened and how do I get them switched back?!?

thanks,
Austin

---

### Post by amsgwp on 2006-08-24
here is a screenshot

[http://www.cashville.net/Screenshot.png](http://www.cashville.net/Screenshot.png)

---

### Post by amsgwp on 2006-08-25
anyone?

---

### Post by amsgwp on 2006-08-25
should this be moved to a different forum mods?

---

### Post by amsgwp on 2006-08-25
digg this article

[http://digg.com/linux_unix/Crazy_Ubuntu_Problem_my_Wired_and_Wireless_got_switched_With_Pics](http://digg.com/linux_unix/Crazy_Ubuntu_Problem_my_Wired_and_Wireless_got_switched_With_Pics)

---

### Post by kuriharu on 2006-08-25
Silly question, but what do you get if you do ifconfig eth1 and again for eth0? Do you get the right IP info?

---

### Post by Paul133 on 2006-08-26
It doesn't seem like that bad  problem. You have wired and wireless working connections, but they're switched in the connection manager. I guess it's just a small bug. Did you file a bug report? Or maybe this isn't a bug?

---

