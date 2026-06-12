---
title: "Finding the Port Application is Trying to Access"
date: 2006-12-27
forum: General Help
---

### Post by smartbei on 2006-12-27
Hello, I am trying to find a program that will let me monitor my application's network accesses'. I just installed PlaneShift and the game is not able to connect to the game's server. My guess is that it is blocked by my router, but I don't know what port to open. Is there a program that can 'listen' to other application's requests?

Thanks!

---

### Post by thelinuxguy on 2006-12-27
This might help:
```
netstat -p -a --numeric | more
```

It will show you the ports your applications are using.

---

### Post by smartbei on 2006-12-27
I managed to solve the problem with:
```
sudo tcpdump
```
and starting the program. Apparently, PlaneShift uses port 7777.

---

