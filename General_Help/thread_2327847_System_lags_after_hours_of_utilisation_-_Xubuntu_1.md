---
title: "System lags after hours of utilisation - Xubuntu 16.04"
date: 2016-06-15
forum: General Help
---

### Post by OverSpeed301 on 2016-06-15
Hello all !

When I start my laptop, there is no problems : no lag, it's not superfluid but it's OK. 


After few hours (~4/5 hours) Ubuntu and Gnome suddenly become very very slow : 3 or 4 seconds of delay when I press Super Key, letters appears 2 ou 3 seconds after I've released the key... Scrolling on text editor (Sublime Text 3) is an horror... If I restart the PC it's OK. I have to restart it 4 times a day to be able to work.


My configuration : 

cat /proc/cpuinfo
```
    
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i3-2328M CPU @ 2.20GHz

```


Sensors : 

```
   
acpitz-virtual-0
Adapter: Virtual device
temp1:        +50.0°C  (crit = +125.0°C)
    
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +50.0°C  (high = +80.0°C, crit = +85.0°C)
Core 0:         +42.0°C  (high = +80.0°C, crit = +85.0°C)
Core 1:         +50.0°C  (high = +80.0°C, crit = +85.0°C)

```

Graphics card : 
```
   
lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])

```

There's no swap since I disabled it, without success. It's not SWAP (8 GB of RAM).
A screenshot of htop, with CPU & memory usage : [http://i.imgur.com/alAdzTK.png](http://i.imgur.com/alAdzTK.png) (gnome-shell normally consumes 15-25% of CPU)
Running Xubuntu 16.04 LTS with LightDM and Gnome Shell. It's a Toshiba Satellite C855-1JN

Any ideas ?
Thanks !

---

### Post by Bucky Ball on 2016-06-15
Well, you have a /swap showing in your htop output so I guess you're right. You didn't succeed in switching it off (Gparted, right click /swap and 'swapoff' or put # in front of the /swap boot line in /etc/fstab). 

I wouldn't advise switching off /swap if your machine is already beginning to lag. I would suggest that perhaps something is getting full over time (maybe there is a problem with RAM) and not clearing itself.

You don't mention how much RAM you do have. If you would, please?

---

### Post by OverSpeed301 on 2016-06-15
Hello

Thanks you, such a fast response ! :D

I have 8 GB of RAM (DDR3). I've commented the swap line in the /etc/fstab. I will reboot and I keep you informed!

---

### Post by Bucky Ball on 2016-06-15
The /swap partition would have nothing to do with this I wouldn't imagine. Your htop was showing it as not used at all at the time of your screen shot.

Think you could be heading down the wrong road here. What raises suspicion this is to do with /swap? I'd be looking in your /tmp folder or checking the logs to see if for some reason you are generating a heap of logfile, it grows and slows down your system, you reboot and the logfile or /tmp directory that's filling is emptied on reboot and voila, your speed is back.

---

### Post by OverSpeed301 on 2016-06-15
Yeap, maybe... I've tried a lot of things so maybe it will works this time ... :)

When the OS lags, I see nothing special : gnome-shell/Xorg taking ~20% of the CPU, the CPU is OK (one core is 100%, all other are ~20-30%), the RAM is always OK, maybe the cache is the culprit ? And I haven't tried iotop to see if the HDD is reading/writing at this moment. It's a 500GB 5400rpm, nothing special. Only Chrome, Sublime Text 3, a Rails server and Spotify are running. I don't use Wifi.

> **Bucky Ball said:**
> The /swap partition would have nothing to do with this I wouldn't imagine. Your htop was showing it as not used at all at the time of your screen shot.

Think you could be heading down the wrong road here. What raises suspicion this is to do with /swap? I'd be looking in your /tmp folder or checking the logs to see if for some reason you are generating a heap of logfile, it grows and slows down your system, you reboot and the logfile or /tmp directory that's filling is emptied on reboot and voila, your speed is back.

It's OK. I'll try to look at the logs when the laptop begins to lag. I will post here if I see anything could go wrong.

Thanks !

---

### Post by Bucky Ball on 2016-06-15
> **OverSpeed301 said:**
> When the OS lags, I see nothing special: ... the CPU is OK (one core is 100%, all other are ~20-30%)

I wouldn't rate one CPU at 100% and the rest up around 30-40% as OK. No wonder it is crawling to snail's pace.

Boot the machine and check immediately what all cores are at for comparison.

---

### Post by OverSpeed301 on 2016-06-15
> **Bucky Ball said:**
> I wouldn't rate one CPU at 100% and the rest up around 30-40% as OK. No wonder it is crawling to snail's pace.

Boot the machine and check immediately what all cores are at for comparison.

Htop just after reboot : 

[ATTACH=CONFIG]269583[/ATTACH]
(previously it was ~30% because I've opened terminal, applications menu, etc... but it dropped quickly)

Laptop started to lag... Here is htop, free -hm, iotop

Htop :
[ATTACH=CONFIG]269584[/ATTACH]

free -hm
```

              total       utilisé      libre     partagé tamp/cache   disponible
Mem:           7,7G        4,2G        1,1G        468M        2,3G        2,7G
Partition d'échange:          0B          0B          0B

```

iotop
[ATTACH=CONFIG]269585[/ATTACH]

In log (tail -f /var/log/syslog && journalctl) I don't see anything strange, there is errors related to GTK with Chrome, but otherwise it's OK.

---

