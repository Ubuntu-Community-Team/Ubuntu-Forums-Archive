---
title: "Cpudyn stopped working"
date: 2008-01-12
forum: General Help
---

### Post by ka9qlq on 2008-01-12
Ok I got rid of powernowd in favor of cpudyn because it lets me lock the cpu speed where I want when I want and everything worked fine for 8 days then I had to do a shut down today because our dip maintenance man killed the power to the building (I'm UPSed but had no idea when power would be back so I logged out and shut down) When power came back I noticed the AMD X2 4800 was at 2.4 ghz so I tolled it to go to 1 ghz and it wouldn't  :o so I try ye old terminal 

```

root@dittohead:~# ./cpumin       <this is a bash script to reset cpudyn to 1ghz
HUP: no process killed
cpudynd: no process killed

```

Ok it didn't load (should have) fine I'll load it

```

root@dittohead:~# cpudyn

[1]+  Stopped                 cpudyn

```

Ok let's try the damon

```

root@dittohead:~# cpudynd
cpudynd version 1.0 Copyright: Ricardo Galli <gallir@uib.es>
cpudynd: CPU frequency control disabled
Error: Nothing to do, exiting

```

 ???

Ok try the the file in init.d

```
root@dittohead:/etc/rc0.d# root@dittohead:/etc/init.d# ./cpudyn
Usage: /etc/init.d/cpudyn {start|stop|restart|force-reload}
```

 Mahdar rikles gitu I tried reinstall complete remove then reinstall nada. What am I overlooking???????

---

