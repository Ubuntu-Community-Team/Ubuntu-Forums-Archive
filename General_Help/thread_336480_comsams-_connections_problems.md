---
title: "comsams- connections problems"
date: 2007-01-11
forum: General Help
---

### Post by virtual_reality on 2007-01-11
I installed comsams, but it doesn't working :( 
when "comsam -i" it says:

Cannot open port, connection failed!
Try to connect to phone...
write() of 4 bytes failed!
No Connection, waiting for phone ready...
Try to connect to phone...
write() of 4 bytes failed!
No Connection, waiting for phone ready...
Try to connect to phone...
write() of 4 bytes failed!
No Connection, waiting for phone ready...
Try to connect to phone...
write() of 4 bytes failed!
No Connection, waiting for phone ready...
Try to connect to phone...
write() of 4 bytes failed!
No Connection, waiting for phone ready...
Tried to connect 5 times. (timeout)


please help, what should I do?:confused:

---

### Post by virtual_reality on 2007-01-12
someone help  me :(

---

### Post by rundy on 2007-01-27
Just been playing with this, depending on what you use to connect your phone to the pc will tell you what command you should use, the default device might not be suitable for you

I used the usb cable and got a little further than you, i used the command
```
./comsams -i -dev /dev/ttyACM0
```

I haven't been able to get any real functionality from the software, but give them a chance i think its still listed as alpha or beta, 

I also tried to use rfcomm as I had a bluetooth dongle
```
./comsams -i -dev /dev/rfcomm0
```

but that didn't get me anywhere, what I'd like to see is the info from comsat used in the gammu project, I was able to pull limited information with gammu/wammu

---

### Post by virtual_reality on 2007-01-28
I used usb cable too but comand ./comsams -i -dev /dev/ttyACM0 doesn't work :(

---

### Post by rundy on 2007-01-30
have you tried watching the system logs to see what device names you get when you plug your phone in?

also I left my phone in the default USB mode which was set to modem

---

### Post by virtual_reality on 2007-01-30
how can I do it?

---

