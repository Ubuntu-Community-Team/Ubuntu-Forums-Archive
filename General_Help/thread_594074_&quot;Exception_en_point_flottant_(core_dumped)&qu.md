---
title: "&quot;Exception en point flottant (core dumped)&quot; ; in  (gutsy)"
date: 2007-10-27
forum: General Help
---

### Post by marcdima on 2007-10-27
i receive this message when i start gbox for ubuntu

gbox 2.1B/Linux@X86 ( Dec  2 2005, 04:06:20 )
OSD (dbox2) IP = 192.168.1.25

desktop:/var/bin$ sudo ./gboxx86

gbox 2.1B/Linux@X86 ( Dec  2 2005, 04:06:20 )
OSD (dbox2) IP = 192.168.1.25
Seasonport=0 speed=9600
mode 03
AU:02/update:01/KeyFile:00 Hash:01 DispECM:01/EMM:01 UDPInit:00 OSD:00
enx_conf = 3 ; reset on zap=0
trying to get online, please wait ...
Exception en point flottant (core dumped)


ubuntu 7.10 (gutsy)
kernel linux 2.6.22-14 generic


i haven't sharing's problem when i use gbox for ubuntu 7.04 


can you help me please,
thank you

---

### Post by marcdima on 2007-10-27
up :(

---

### Post by noelferreira on 2007-10-29
i have experienced exactacly the same problem. 
And it seems there'll be no new gbox version soon :(.

noel ferreira

---

### Post by piefav on 2008-01-03
I solved,
the problem is the file /etc/nsswitch.conf

I change the line
```
hosts: files dns mdsn
```

now run !!!

---

