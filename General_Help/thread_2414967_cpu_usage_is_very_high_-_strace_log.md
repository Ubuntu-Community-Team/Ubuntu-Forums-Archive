---
title: "cpu usage is very high - strace log"
date: 2019-03-18
forum: General Help
---

### Post by mixtutor on 2019-03-18
Hi, i am facing a strange issue with wine. I am using ubuntu 14, 17 and 18 and in all version same thing, app which works perfeclty suddenly slow down, and i see that use too much CPU. First, i was thinking that memory is the problem, but now i am thinking that cpu is main problem.
I have a various hardware configuration, all have 4GB ddr3 or ddr4 RAM, and all have intel cpu dual core. GPU mainly intel integrated, but have AMD RADEON and NVIDIAs
I tried with ryzen3 also, but same there. Dont seem that hw is problem. I tried and reinstall whole system.
Things I tried:


```

export __GL_THREADED_OPTIMIZATIONS=1


export GPU_MAX_HEAP_SIZE="100"


export GPU_MAX_ALLOC_PERCENT="100


cpulimit -l 20 wine MyProgram.exe


%sudo   ALL = (ALL) NOPASSWD: /usr/bin/cpulimit
echo 3 > /proc/sys/vm/drop_caches && swapoff -a && swapon -a
taskset --cpu-list 1 cpulimit -l 20 wine MyProgram.exe




```


Also tried things from:
[Link]("https://onthim.blogspot.com/2017/07/stop-ubuntu-from-freezing-completely.html")
[Link1]("https://onthim.blogspot.com/2018/10/opengl-texture-compression-library-for.html")


Don't have idea what to try.
maybe someone had similar issue?
I installed wine 
```
 wine


        sudo dpkg --add-architecture i386
        sudo add-apt-repository ppa:wine/wine-builds
        sudo apt-get update
        sudo apt-get install --install-recommends winehq-devel
        winecfg
```
```
       sudo dpkg --print-foreign-architectures 
i386
```

```
ps -w -e --no-header -o uid,user  | sort -u   | while read uid user; do echo -e "$user\t"$(ps --no-headers -u $uid --cumulative -o time  | sed -e s/:/*3600+/ -e s/:/*60+/ | paste -sd+| bc);done
root    183
myuser  1214



```
So, it consumes more CPU time than root (MyProgram.exe is opening with myuser, not root)

I did a strace in about 5sek and make me 15MB log.
found a bunch of this **75986:recvmsg(9, {msg_namelen=0}, 0)          = -1 EAGAIN (Resource temporarily unavailable)**


> poll([{fd=9, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=9, revents=POLLOUT}])
writev(9, [{iov_base="<\3\2\0~\362o\0047\0\4\0\177\362o\4\2\0`\4\0\0\0\0", iov_len=24}, {iov_base=NULL, iov_len=0}, {iov_base="", iov_len=0}], 3) = 24
recvmsg(9, {msg_namelen=0}, 0)          = -1 EAGAIN (Resource temporarily unavailable)




---

### Post by mixtutor on 2019-03-19
anyone?

---

