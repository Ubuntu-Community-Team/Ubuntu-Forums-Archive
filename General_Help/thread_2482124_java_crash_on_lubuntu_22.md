---
title: "java crash on lubuntu 22"
date: 2022-12-21
forum: General Help
---

### Post by mixtutor on 2022-12-21
java error [https://paste.ubuntu.com/p/fHF8ThzwYS/](https://paste.ubuntu.com/p/fHF8ThzwYS/)

problem is that java is crashing on new lubuntu 22.10 on my 500+ upgraded machines. This is hw info

```
sudo dmidecode | grep -A 9 "System Information"System Information
        Manufacturer: ASUSTeK COMPUTER INC.
        Product Name: MINIPC PB62
        Version: To be filled by O.E.M.
        Wake-up Type: Power Switch
        SKU Number:
        Family: Vivo PC



```
I am using java jre1.8.0_151, also tried with newest jre, but no luck. Tried to prirotize process and to make it use all cores

```
taskset -cp 3496
pid 3496's current affinity list: 0-11

sudo renice -20 3496
3496 (process ID) old priority 0, new priority -20

```
but no luck. Any ideas what can i do, and what is problem with java and lubuntu 22....

---

### Post by ActionParsnip on 2022-12-21
What is the output of
```

java --version

```

---

### Post by mixtutor on 2022-12-21
```
java -versionopenjdk version "1.8.0_352"
OpenJDK Runtime Environment (build 1.8.0_352-8u352-ga-1~22.10-b08)
OpenJDK 64-Bit Server VM (build 25.352-b08, mixed mode)



```

also tried with local java  jre1.8.0_151, not installed via apt, just exist in folder. On older lubuntu systems, 18.04 for example i open my .jar with command:

```


/home/user/jre1.8.0_151/bin./java -jar ~/example/example.jar



```

so this version with local java works very well, Then i update to 22 and have this kind of issues.
I can't revert 'cause of another things installed and must be on 22.


added: memory info about process
[https://paste.ubuntu.com/p/rM5kPjQbyx/](https://paste.ubuntu.com/p/rM5kPjQbyx/)

---

### Post by ActionParsnip on 2022-12-21
Is it OK with Oracle Java or is it known to work OK with OpenJDK?

---

### Post by mixtutor on 2022-12-22
I just used it with java jre

---

