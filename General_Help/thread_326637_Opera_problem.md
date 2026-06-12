---
title: "Opera problem"
date: 2006-12-27
forum: General Help
---

### Post by Coop on 2006-12-27
Hello
I have an Opera web browser problem problem:
First I installed Opera 9 from Automatix,and then I downloaded Opera 9.1 deb from Opera's website.I uninstalled Opera 9 and installed Opera 9.1,and when it installed Opera 9.1 it said it conflicts with installed package 'Opera".

And when I try to start Opera it doesn't start it.

Please tell me what to do.

Regards Coop

---

### Post by ~LoKe on 2006-12-27
Go to the directory with the opera .deb
```
sudo dpkg -r opera
```
```
sudo dpkg -i opera*
```

---

### Post by Coop on 2006-12-27
Hello
~LoKe I did it but Opera doesn't start.
Also,when I try to start Opera from the terminal it says:```
opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
opera: It seems another instance is running because this file is locked:
opera: /home/coop/.opera/lock
```
Why isn't it starting it?
Please tell me what to do.
Regards Coop

---

### Post by ~LoKe on 2006-12-27
```
sudo rm ~/.opera/lock
```

---

### Post by Coop on 2006-12-27
Yes!it worked!Opera started!
Thank you ~LoKe.
Regards Coop

---

### Post by ~LoKe on 2006-12-27
Not a problem. =]

---

