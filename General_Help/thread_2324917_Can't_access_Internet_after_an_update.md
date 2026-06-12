---
title: "Can't access Internet after an update"
date: 2016-05-17
forum: General Help
---

### Post by dallase1 on 2016-05-17
It seems that after I installed a recent update I was no longer able to access the INTERNET but luckily I have a program called time shift that is like Windows Restore and I was able to restore from a a earlier point before the update that messed up my Internet access. I would get a server not found error and when I checked the wired connection it did not report anything wrong so I tried connecting VIA Wireless, it say the WIFI connection and successful logged into the router but I still got the Server Not Found Error. Since I don't have access to the Internet I can't install anymore updates that might fix the problem.

I have Cylon Linux Release 12.04 LTS (precise) 32-bit Kernel Linux 3.2.0-102-generic-pae GNOME 3.4.2

---

### Post by QDR06VV9 on 2016-05-17
Yours is not a clear-cut situation, so we go by successive approximations.

First, issue these commands:
```
sudo service network-manager stop
    sudo ifconfig eth0 down
    sudo ifconfig eth0 up
    sudo dhclient eth0
```
and see whether this works. In any case, re-issue

```
sudo service network-manager start

```
Fingers crossed

---

### Post by Bashing-om on 2016-05-17
dallase1; And Also ...

There is a current bug in updates that breaks network-manager:
see: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634) 

If this is your predicament, there are a number of fixes around.
Perhaps the easier is:
[http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841](http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by dallase1 on 2016-05-17
Yup that worked.
Thanks:D

---

