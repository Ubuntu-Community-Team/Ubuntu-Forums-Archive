---
title: "I Spoke Too Soon. Restricted Extras Download is Still Blocked."
date: 2017-12-30
forum: General Help
---

### Post by wbee on 2017-12-30
Hello,

I'm embarrassed. I marked a previous thread solved prematurely. My bad.

I tried again to install ubuntu restricted extras and ended up with this result,exactly as before.

That is,I tried to install the packages and when I got to the Microsoft permissions page,I hit enter but it did nothing,so I close it. Should I have mouse swiped it to change color and then hit enter? Is that the trick?

Anyway,here is the result:

```
 wbee@wbee-A780L3C:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for wbee: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
wbee@wbee-A780L3C:~$  
```

How do I clean up my mistake?

Thanks.

---

### Post by wbee on 2017-12-30
I opened the software updater and it hung,displaying the message, "Waiting for apt-get to exit".

---

### Post by RobGoss on 2017-12-30
You can always unmarked that thread if you have not found the answer you are looking for

---

### Post by Frogs Hair on 2017-12-30
Try the following commands.

```
sudo fuser -vki /var/lib/dpkg/lock; sudo dpkg --configure -a
``` ```
sudo apt update && sudo apt upgrade
```

---

### Post by wbee on 2017-12-30
Thank you,Frog's Hair. Those worked.:-)

---

