---
title: "High CPU Load and enormous logs"
date: 2008-02-14
forum: General Help
---

### Post by Showan2 on 2008-02-14
hi

Today I got a message that my / partition was full. This seemed strange because yesterday there was about 4 GB free. Next thing I noticed that my CPU load was 100 % all the time. So I found the problem: something is constan writing to 3  logs: kern.log, sys.log and another

they are all over 1.2 Gb now


what can I do? I can't open the logs

thanks

---

### Post by funkytwig on 2008-02-14
You need to post the last 50 or so messages from the log files for people to be able to help you.

---

### Post by bb002 on 2008-02-14
try using the tail command on them.
such as:
```

tail /var/log/kern.log

```
hopefully it will give you some insight as to what is up.
My guess is you either got a piece of hardware going bad or an application of some sort spamming the logs.

I have a usb port that went bad on my pc. connecting anything in it causes the same type of thing you are suffering. I get hundreds of USB connect/disconnect messages a second in the kern.log whenever that port gets used. Though I didn't notice any kind of abnormal cpu usage when this happens just a lot of disk activity for no apparent reason and a USB device that isn't working. :P

---

### Post by nemilar on 2008-02-14
Can you post what process is using up your CPU?  Run the command:

```
top
```

in a terminal to find out.  The upper commands are the ones using the most resources; it'll say how much CPU each process is using.


You also delete the logs (via sudo rm [logfiles]) and then run:
```
sudo /etc/init.d/sysklogd restart
``` 

Which will let the 'df' command notice the changes (otherwise it won't report the newly freed space, since the system logger will be keeping those files open).

Once we know what process is using up all the resources, it'll be much easier to figure out the problem and a solution.

---

### Post by Showan2 on 2008-02-14
hi

looks like some really strange stuff is going on here:

> joan@joan-desktop:~$ tail /var/log/kern.log
Feb 14 17:01:34 localhost kernel: a aanaanana aana aa aana aanaana aa aanaana aanaana aana aanaana aanaanaana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aanaana aanaanaana aana aa aana aana aanaanaana aanaaanaanana aant=1384878ana aanaanaana aana aanaanaana aana aanaana aanaana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aanaana aanaana aana aana aanaana aana aanaanaana aana aanaana aana aana aana aanaa aanana aana aana aana aana aana aana aana aana aana a aanaana aana aanaana aana aana aana aana aana aanaanaana aana aana aana aa aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aanaana aana aana aana aanaana a aanaa aanaana aanaana aanaana aana aanaana aanana aanaana aa aana aanaana aana aana aanaana aana aa aana aana aana aana aana aana aana aana aanaana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aa aana aana aana aana aana aanaana aana aanaana aana aanan
Feb 14 17:01:34 localhost kernel: na aana aanaana aana aana aanaana aana aanaana aana aanaa aana aana aana aana aana aanaana aana aana aana aana aanaana aana aana aana aanaanaanaana aanaana aanaanaana aaana a aa aa aa aa aa aanaa aa aa aa aa aa aa aa aa a aanaana aanaana aanaana aana aana aanaana aana aanaana aana aana aana aana aana aana aana aanaanaanaana aana aana aana aana aana aanaana aanaana aana aana aanaana aana aana aanaana aana aaanaana aana aana aana aana aana aana aana aana aana aananaana aanaana aana aana aana aana aana aana aana aana aana aanaana aanaana aana aana aana aana aana aana aana aana aa aana aana aana aana aana aana aana aana aana aana aana aana aa aana aana aa aananaana aana aana aana aana aanaana aana aanaana a aa aana aa aana aa aana aanaanaanaana aa aa aana aana aa aana aa aana aana aana aa aana aanaa aana aanaa aana aa aana aa aana aa aanaa aanaanaa aanaana aanaa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aana aana aanaanaana aana aana aa aanaanaa aanaa aanaanaana aa aana aa aana aa aan
Feb 14 17:01:34 localhost kernel: na aa aana aanaa aana aa aana aana aa aana aana aa aana aana aa aana aana aa aana aa aanaanaanaana aa aana aa aana aana aana aana aana aana aanaanaana aana a aa aana aana aana aana aana aa aana aana aana aana aanaana aana aanaana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aana aanaaananana aa aana aana aa aana aa aanaana aanaana aanana aa aana aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa aa a aa aanaana aana aana aa aana aanaana aana aanaanana aana aanaana aana aanaanaa aana aana aana aana aana aanaana aa aanaanaanaana aana aana aana aanaana aana aa aana aana aanaanaana aanaana aana aana aana aana aanaana aana aana aana aanaa aanana aanaana aana aana aana aanaanaana aana aanaana aana aanaana aana aana aana aana aana aanaanaana aana aanaanaana aana aa aana aana aana aana aanaanaanaana aana aa
Feb 14 17:01:34 localhost kernel: aaaanaanaanaanaanaana aanaana aana aana aanaanaana aanaana a aana aana aana aana aana aana aana aana aana aanana aanaana aana aana aana aana aana aanaana aana aanaanaana aanaanaana aanaanaanaanaana aanaana aana aana aana aana aana aana aana aana aana aana aana aana aanaanaana aana aana aana aana aanaana a aanaana aana aana aana aana aana aana aanaanaana aa aana aanaana aana aanaana aana aanaanaana aana aana aanaana aanaanaana aana aana aana aana aana aanaanaana aa aana aana aana aana aana aana aana aana aanaanaana aana aana aana aana aana  aanana aanaana aana aanaana aana aana aana aanaana a aana aana aana aana aanaana aanaana aana aana aana aana aana aanaana aanaanaana aana aana aanaana aana aana aanaana aana aana aana aanaanaana aana aana aana aana aana aana aana aana aana aana  aana aanaa aana aa aana aa aana aa aana aa aanaana aanaa aana aana aanaa aana aa aana aa aana aa aana aa aana aa aana aana aana aa aana aa aana aa aana aa aanaanaa aanaa aanaanaa aanaana aanaa aana aana 
Feb 14 17:01:34 localhost kernel: a aa aa aana aa aanana aana aana aana aanaana aana aana aana aana aana aanaana aana aana aana aana aana aana aana aanaana aana aana aana aana aana aana aana aana aana aana aana aana aana aanaanaana aant=1384878ananaana aa aana aanaana aana aanaanaana aana aanaa aa a aanaanaana aa aanaana aana aana aana aana aana a aana aanaana aana aa aana aa aana aana aa aana aana aa aanaa aana aa aanaanaa aanaana aana aana aanaanaa aanaanaanaanaana aanaanaana aa aanaanaanaanaanaana aana aanaa aanaana aana aanaa a aana aanaana aana aa aana aana aanaa aana aana a aana aana aanaanaanaanaana aa aana aanaanaana aa aana aanaanaa aana aa aanaanaanaana aa aana aanaanaanaanaana aana aanaanaana aanaana aa aana aana aanaa aanaana aana aa aana aanaana aa aananana aana aana aanaana aana aana aana aana aana aana aanaana aana aana aana aanaana aana aanaana aana aana aanaana aana aana aana aanaana aana aanaana aanaanaana aana aana aana aana aanaana aana aana aana aana aana aanaana aanaana aanaana aa aanant=1384
Feb 14 17:01:34 localhost kernel: 616, limit=31776507
Feb 14 17:01:34 localhost kernel: [ 2464.183643] attempt to access beyond end of device
Feb 14 17:01:34 localhost kernel: [ 2464.183645] sda1: rw=0, want=13848781616, limit=31776507
Feb 14 17:01:34 localhost kernel: [ 2464.183650] attempt ta aanaana aa aanaana aana aana aana aanaa a ant=13848781616, limit=31776507
Feb 14 17:01:34 localhost kernel: aaana aananana aana aanaanaana aana aanaana aa aana aa aanaana aana aanaana aana aana aanaana aana aanaana aana aana aana aanajoan@joan-desktop:~$ 


and
> joan@joan-desktop:~$ top

top - 18:11:51 up 4 min,  2 users,  load average: 3.68, 2.10, 0.86
Tasks: 146 total,   4 running, 141 sleeping,   0 stopped,   1 zombie
Cpu(s):  9.0%us, 90.9%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.1%hi,  0.0%si,  0.0%st
Mem:   2060768k total,   608872k used,  1451896k free,    47436k buffers
Swap:  2289188k total,        0k used,  2289188k free,   239776k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                        
 5755 joan      20   0 31788 1876 1620 R   95  0.1   1:02.75 apt-cache                                                                                                      
 4839 root      20   0  8092  580  468 R   66  0.0   1:59.84 dd                                                                                                             
 4841 klog      20   0  4900 1580  388 S   34  0.1   1:08.81 klogd   

....


Any clues? Thanks

---

### Post by bb002 on 2008-02-14
hmm...looks like apt-cache is the source. run this in a terminal
```
killall apt-cache
```
That program should terminate pretty fast when running as you user account. Your user account shouldn't have rights to a directory it wants to write in. So I don't understand why it is running like that...


I don't like the message about reading past the end of the device. I'd run a filesystem check on /dev/sda1. Maybe even run a bad sector scan on your harddrive at /dev/sda. Unfortunately both of these are things i'm not really experienced with doing in linux. I rather wait for someone that knows more than I do to help you run the flesystem/hdd scans.

[edit]
run top again and post what is says after killing apt-cache.

---

### Post by Showan2 on 2008-02-15
hi

I ran an fsck on sda1, it repaired many errors and now all is back to normal!!

strange because i did an fsck on it only a few weeks ago


many thanks to all!

---

