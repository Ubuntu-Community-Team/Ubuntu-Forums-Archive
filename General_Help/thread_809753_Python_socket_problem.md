---
title: "Python socket problem"
date: 2008-05-27
forum: General Help
---

### Post by Roberto_Lapuente on 2008-05-27
Hi, I'm trying to listen a port with python on a debian server. I try the program in ubuntu and it worked but in debian it gives back: 
socket.error: (99, 'Cannot assign requested address')
my code is:

```
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
sock.bind((socket.gethostname(), 6002))
sock.listen(5)
```

please help

---

