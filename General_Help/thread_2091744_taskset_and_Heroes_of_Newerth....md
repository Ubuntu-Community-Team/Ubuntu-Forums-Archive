---
title: "taskset and Heroes of Newerth..."
date: 2012-12-05
forum: General Help
---

### Post by MutantJohn on 2012-12-05
Hello All,

So recently I discovered that you can control which processor a certain thread has an affinity for through taskset. At least, I'm assuming it's a thread, right? 

Either way, I have the game Heroes of Newerth and when you install it, it generates the executable binary hon-x86_64.

So at the terminal, I'll type:

```
tasket -c 3 ./hon-x86_64
```

and when I run 

```
taskset -p <HoN's PID here>
```

I get that the affinity is for core 1, the 2nd core, and not the 4th. I can use

```
tasket -p 03 <HoN's PID here>
```

and then it'll finally be on the 4th core and stay there. But my question is, why does my initial taskset command not work? If I leave out the "./", it'll tell me there's no such file of directory as hon-x86_64 so it seems like I HAVE to execute it with taskset.

---

### Post by MutantJohn on 2012-12-06
So I've checked around I've heard it might have something to do with the scheduler. As in, I think what I'm actually doing is launching HoN on the 4th core but afterwards, the scheduler just treats it like a normal application and distributes it as it was natively coded to do so, namely putting a higher priority on the 2nd core to make things easier for the 1st which, using htop, is the one that is most heavily taxed by everything else that isn't HoN.

---

