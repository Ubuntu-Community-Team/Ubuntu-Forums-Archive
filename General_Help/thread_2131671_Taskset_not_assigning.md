---
title: "Taskset not assigning"
date: 2013-04-02
forum: General Help
---

### Post by Code9 on 2013-04-02
I am running this on Ubuntu Server 12.10. I am trying to set a process to only operate on two cores of my CPU. I am running the following command. 

```
taskset -pc 0,1 5090
```

and I get this as the result. 

```
pid 5090's current affinity list: 0-7
pid 5090's new affinity list: 0-7
```

It doesn't seem to be sticking. Any help is appreciated.

---

### Post by Doug S on 2013-04-02
Hmmm.... It seems to work as expected for me. However, I only have 12.04 and 13.04 servers at the moment, no 12.10.```
doug@s15:~$ taskset -pc 0,1 24792
pid 24792's current affinity list: 0-7
pid 24792's new affinity list: 0,1

```That was on a 12.04 server, and the process is a mindless single thread CPU hogging program.

---

### Post by Code9 on 2013-04-02
Would the virtualization affect it? I am using an OpenVZ VPS.

---

### Post by Doug S on 2013-04-08
I happened to be doing stuff on a virtual machine (kvm) today, and it still worked:```
doug@virt64-01:~$ taskset -pc 0,1 1810
pid 1810's current affinity list: 0-3
pid 1810's new affinity list: 0,1
```I don't know about the VM type you are using.

---

