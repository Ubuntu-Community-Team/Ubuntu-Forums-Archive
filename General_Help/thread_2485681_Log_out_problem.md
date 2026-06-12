---
title: "Log out problem"
date: 2023-04-05
forum: General Help
---

### Post by effesan83 on 2023-04-05
Hi every one , I'm Ferdinando i use linux since high school, but very intensive when i was studying it in university..i try a few distro and since some years i only use xubuntu in my old laptop and now also ubuntu on desktop...but i noticed from about some week a problem:
ubuntu start without log in (ok this is a security underestimating problem), but the system log me out several times every day, from using libreoffice, click on firefox or anything also when using browser and create me problem when i was in a transaction shop of a gel for inflamation, contracture and nerve(tendini) problem.
Now i'm tired of send about 3 bug reports every time i kick out  without a solution...i'm wait for the next release hoping better performance
this hp desktop have a intel i7-10700f cpu,  an amd gpu rx540 or rx550, ssd nvme 512gb with 6 partition(for other software or product i damn need to use win 11)
i hope to have an opinion or a tips,
thanks

---

### Post by TheFu on 2023-04-05
Is TMOUT set?

---

### Post by effesan83 on 2023-04-08
i try to find in "/etc/profile" , or "somewhere/.bash_profile" but other file or with grep i can't find this variable..but after few seconds ago and i start 5-7 min before, i try to open notepaddqq and crash kick me out in some bug report i find these:<br>"<br>gnome-shell 43.1-0ubuntu1 signal 7 kernel 5.19.0-38.39-generic 5.19.17<br><br>tracker-miner<br>"<br>but i can't understand why, and i haven't problems with my laptop with amd apu and gpu, older, with xubuntu and i put the kernel 6.0 maybe...no problem<br>i hope nextr release ubuntu use this kernel, i think before now i coudn't had problem with fedora,mandriva,centos, and other distros so the problem is some thing in this hardware or the updates i install<br>

---

### Post by TheFu on 2023-04-08
```
echo $TMOUT
```
is the easy way to check.

HTML formatting isn't allowed here. Use BB-code or the editor buttons, if you prefer.  Though sticking with default fonts is best. 
You can edit the prior post to make it readable.

---

### Post by MAFoElffen on 2023-04-08
It would be useful if you posted the links to those Bug Reports that you said you sent. Also if you mentioned something about the Version of Ubuntu that you are running, and the hardware you are running it on. 

Trying to translate what you have said.

From what you described, I might guess that you might have older hardware with limited resources or are trying too run to much at the same time for the resources you have. 

Xubuntu does not use Gnome. It uses XFCE. So from that, in the past you ran XFCE that used lessor resources. Your error occurs on Gnome Shell, version 34.1, which is dependent on tracker-minerfs... which doesn't run well on older hardware with limited resources.

The thing to do would be to look at what you are running Ubuntu on, and see if there is a true bug, or if the system is just "limited". Please post the results of these commands, posted within CODE Tags:
```

uname -r
lsb_release -d
free
grep 'model name' /proc/cpuinfo | head -n 1
ps -eo pid,ppid,cmd,comm,%mem,%cpu --sort=-%mem | head -n 10

```
If your system is older, and has the resources to run Ubuntu, there is a work-around to disable minor-trackerfs to make it not crash from that, and be faster. If not, then maybe you might have to use a "lighter" flavor of Ubuntu... But lets lot what your system stats says first.

---

