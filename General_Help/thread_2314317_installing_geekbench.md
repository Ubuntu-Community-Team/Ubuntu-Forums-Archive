---
title: "installing geekbench"
date: 2016-02-20
forum: General Help
---

### Post by ahmad25 on 2016-02-20
Hi guys, I'm kinda new with Linux. Just started using Ubuntu 15.10 for a few days. I knwo that we can download and install program from the software center but I noticed there's no geekbench. Im trying to do comparison benchmark between ubuntu and windows (geekbench works in both). However after i download an extract the file,  I cant seem to install the app. There's 4 file and the only file i can execute is geekbench_x86_64. Everytime i write  (./geekbench_x86_64) in terminal it says that it's in tryout mode and i cant use the command (make and sudo make install). Can someone help me with this. Am i doing something wrong or any steps I accidentally skipped?

---

### Post by deadflowr on 2016-02-20
Fairly simply really.
You need the 32-bit libraries for libc6 and libstdc++6.
So if not installed go ahead and try to install those with
```
sudo apt-get install libc6:i386 libstdc++6:i386
```
Then in for the command, use just the geekbench.
Instead of the geekbench_x86_64

They guide you about it on their own site:
[http://support.primatelabs.com/kb/geekbench/installing-geekbench-on-linux](http://support.primatelabs.com/kb/geekbench/installing-geekbench-on-linux)

---

### Post by ahmad25 on 2016-02-20
> **deadflowr said:**
> Fairly simply really.
You need the 32-bit libraries for libc6 and libstdc++6.
So if not installed go ahead and try to install those with
```
sudo apt-get install libc6:i386 libstdc++6:i386
```
Then in for the command, use just the geekbench.
Instead of the geekbench_x86_64

They guide you about it on their own site:
[http://support.primatelabs.com/kb/geekbench/installing-geekbench-on-linux](http://support.primatelabs.com/kb/geekbench/installing-geekbench-on-linux)
 

Oh god! Thanks man! I actually read the guide but I really have no idea about the 32-bit library thing so i ignored it! I wanna ask one more question if that's ok with you. Do i have to type the 32bit library code for everytime i want to install a software that is not on the Ubuntu Software Center?

---

### Post by deadflowr on 2016-02-20
> **ahmad25 said:**
> Oh god! Thanks man! I actually read the guide but I really have no idea about the 32-bit library thing so i ignored it! I wanna ask one more question if that's ok with you. Do i have to type the 32bit library code for everytime i want to install a software that is not on the Ubuntu Software Center?

Those are in the software center.
You simply need to click on the *show more technical item*s at the bottom of whatever you search for.
example if you run a search for gedit, in the result page look at the bottom and you will see a show some-number technical items.
click on that and the result page will reload to show all results related to your query.
And those results will be more detailed with the real package name underneath each result's name the software center has given it.
Makes more sense when you do it, than I can explain.

---

### Post by ahmad25 on 2016-02-20
> **deadflowr said:**
> Those are in the software center.
You simply need to click on the *show more technical item*s at the bottom of whatever you search for.
example if you run a search for gedit, in the result page look at the bottom and you will see a show some-number technical items.
click on that and the result page will reload to show all results related to your query.
And those results will be more detailed with the real package name underneath each result's name the software center has given it.
Makes more sense when you do it, than I can explain.


Thanks for the information! :D:D

---

### Post by coldraven on 2016-02-20
> **deadflowr said:**
> Those are in the software center.
You simply need to click on the *show more technical item*s at the bottom of whatever you search for.
example if you run a search for gedit, in the result page look at the bottom and you will see a show some-number technical items.
click on that and the result page will reload to show all results related to your query.
And those results will be more detailed with the real package name underneath each result's name the software center has given it.
Makes more sense when you do it, than I can explain.

Or install the Synaptic Package Manager, think of it as Software Centre Pro. You cannot use both at at the same time as they are just different front ends of the "apt" package system.

Look for it in the Software Centre or just do this:
```
sudo apt-get install synaptic
```

How to here:
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

