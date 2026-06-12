---
title: "Old laptop system ?"
date: 2015-05-25
forum: General Help
---

### Post by nu2this2 on 2015-05-25
Hello,

Purchased an old laptop with Hardy Heron installed. It works O.K But I would like to install the latest version that the laptop could accommodate  Would like to know the specs of this unit. Can anyone explain how to do this? 

Thanks

---

### Post by slickymaster on 2015-05-25
In a terminal window run```
cat /proc/cpuinfo /proc/meminfo
df -h
```I don't remember now if Hardy already shipped [lswh]("http://linux.die.net/man/1/lshw") but you can try it and check it```
sudo lswh
```

---

### Post by grahammechanical on 2015-05-25
Have all the logos and labels been removed from the machine? Somewhere there should be a sticker giving the manufacturer's name and a product code. From there you do a web search. This command will tell if the machine can run Ubuntu with Unity

```
/usr/lib/nux/unity_support_test -p
```

I am not sure what result you will get on a version of Ubuntu that old. But if you do not see Yes, then you will need Xubuntu or Lubuntu or may be Ubuntu Mate. I do think that you should be looking at those alternatives anyway.

This command will show what hardware the machine has

```
sudo lshw
```

This command will create a profile of the hardware and store it as a file called hardwareprofile.html which can be opened in the web browser

```
sudo lshw -html > hardwareprofile.html
```

Regards.

---

### Post by nu2this2 on 2015-05-25
Thanks to both :p

---

### Post by slickymaster on 2015-05-25
You're welcome.

Please don't forget to mark the thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), so other people searching the forums know that it provides a working solution.

---

