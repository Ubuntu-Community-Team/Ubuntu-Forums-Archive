---
title: "Very slow BEFORE boot lubuntu-core 14.10"
date: 2015-02-28
forum: General Help
---

### Post by Nguyen_Duy_Thinh on 2015-02-28
Aloha guys,

I just installed Lubuntu-core 14.10 on my old notebook. After install, it starts to login screen in about _70 seconds._ 

But when I remove the power charge (and battery is broken so my notebook doesn't have battery), and plugin power charge again and power on, it takes _more than 6 minutes_ to login screen. 

"dmesg" code shows 72 seconds boot, so I go to /etc/default/grub , change "quite splash" to "text" and reboot to see what actually happends. 

The result: 
--> BIOS start screen (5 seconds, with DEL, F11 to boot, etc...) 
--> **BLACK SCREEN 5 minutes [COLOR=#b22222]with-the-data (hard drive)-light-flashing-continuing[/COLOR]** 
--> start booting (70 seconds, i can see details because I made grub to "text" mode above) 
--> login screen
(total time: more than 6 minutes)

More info: 
I make partition **/boot** to my SSD(sdb) and** /(root)** to my SD-card(sdc) (see code below), both are connected when booting,[COLOR=#b22222][B] I guess something wrong here.
[/B][/COLOR]```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        15G  3.2G   11G  23% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            234M  4.0K  234M   1% /dev
tmpfs            49M  916K   48M   2% /run
none            5.0M  4.0K  5.0M   1% /run/lock
none            244M   72K  244M   1% /run/shm
none            100M   28K  100M   1% /run/user
/dev/sdb6       464M  2.3M  433M   1% /tmp
/dev/sdb2       180M   36M  132M  22% /boot
/dev/sdb7       755M   89M  612M  13% /opt



```

I hope you can help me find out what happens in that 5-minute black screen so that I can completely get rid of it.
Thank a lots!!

---

