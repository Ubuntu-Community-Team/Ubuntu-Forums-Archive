---
title: "problems with k3b"
date: 2006-10-22
forum: General Help
---

### Post by creepingdeath086 on 2006-10-22
Ive been having problems with k3b starting up when I go to run it from either terminal or from any menu. When I run it in terminal it returns this:

martin@BetterWork:~$ k3b
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

I am unsure as to what this means, I dont post here often, but have used linux for years. Is this a system problem that I am having, or should it be reported as a bug? Thankyou.

---

### Post by MarkoSK on 2006-10-29
i got the same problem...i jsut upgraded from dapper to edgy...and now i have burning problems in ubuntu...i tried few burning programs...and can't burn with any off them...especialy k3b...(tryed dvd's/cd's...all )

if any one has any idea that would be great :!?

---

### Post by MarkoSK on 2006-10-29
aperantly i fixed this problem---
all i did was:

sudo apt-get --reinstall install kdelibs

and

sudo apt-get --reinstall install kde

and after that everything works fine again :D

---

### Post by MarkoSK on 2006-10-29
except that now dvd's that i burned with k3b become unreadable... :( argh...
ubuntu doesn't recognize the burned dvd's no more :(


wtf??

---

### Post by creepingdeath086 on 2006-10-30
I think upgrading to Edgy fixed my problem, however, now I dont have sound.

---

