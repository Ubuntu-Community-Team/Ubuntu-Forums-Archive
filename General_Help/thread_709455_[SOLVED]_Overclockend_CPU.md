---
title: "[SOLVED] Overclockend CPU"
date: 2008-02-27
forum: General Help
---

### Post by arashiko28 on 2008-02-27
Recenly my CPU has been overworking at 100% with no apparent reason. Meaning that I may have a couple of docs open, amsn and the system monitor shows a CPU history at 100%. This causes overheating and the computer shuts down even with an external fan. This is a laptop and I have a fan the keeps it fresh. But even with it, it say "Critical Temp reached 94ºC, shutting down" (might be 95, 96). I know this is to protect the computer and that's not the complaint. But the overworked CPU, recent changes, Installed Acroread 8 and a couple of updates.

I don't game, only work with several documents at the time, music, video (not together), chat and internet, so I don't understand why it's doing this. Please help, this causes the computer to be extremely slow (as windows slow) I'm already used to the super speed of Linux. and takes too long to restart or shutdown manually.

HELP!!!!

---

### Post by Sam Lars on 2008-02-27
If you have a CPU, etc. graph on your panel, you can open System Monitor through there.  Look at the processes sorted by CPU to see what is using it all.
Alternatively, and if that doesn't show anything, you can run
```
top
```
on the command line to find the culprit.

---

### Post by arashiko28 on 2008-02-27
Ok, I got a lot of numbers, changing numbers, and don't understand nothing of it. I'm not a total noob, but I'm not an IT either :confused: please be a bit more explicit.

---

### Post by Sam Lars on 2008-02-27
Ok, here's an example from me right now, in top:
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
32139 boinc     34  19 75084  41m 3600 S 80.9  5.5  34:47.61 wcg_hcc1_img_5.
```
It's all labeled.  %CPU shows that some process is using 80.9 percent of my processor.  That process is under COMMAND, which is the wcg_...
System Monitor is easier to understand.
You can sort by %CPU again...and the Process Name is what you're looking for.

So, what process/command seems to be using an excessive amount of CPU?

---

### Post by arashiko28 on 2008-02-27
khubd it's eating up my processor at 97%. It's so slow that even takes time for terminal to be ready to use. But I don't know this command, what does it do?

---

### Post by arashiko28 on 2008-02-27
Ok, I found out, the problem is a Bug caused by Ekiga. I have never used that:confused:
is bug #32164, I'm looking for a solution, if someone has it, please help!

---

### Post by Sam Lars on 2008-02-27
If you don't use it, remove it as I have. :)

---

### Post by arashiko28 on 2008-02-27
:shock::shock: It says that will remove gnome and gnome desktop environment, I don't want that to happen, how do I remove it without so much pain?

---

### Post by Sam Lars on 2008-02-27
Those are meta-packages.  They just depend on all basic Gnome environment programs and such.  Removing them shouldl not hurt anything.

---

### Post by arashiko28 on 2008-02-27
it seems as it worked thanks a lot.:popcorn:

---

### Post by arashiko28 on 2008-02-27
Problem wasn't solved. I removed the Ekiga and still my mouse doesn't work and that damn thing khubd it's still eating up my CPU! HELP!!!!

---

### Post by arashiko28 on 2008-02-27
This bug solutions does not work, please help!!!!
Solution Temp:
* Open console
* $ps -ef | grep khubd
* $kill NumberProcess_khub
* In 2 minutes ++, $kill -9 numerProcess_khub
* Add 2 minutes, $sudo killall -9 khubd

>  kill 1972_khubd
bash: kill: 1972_khubd: arguments must be process or job IDs
> sudo killall -9 1972_khubd
1972_khubd: no process killed


---

### Post by Sam Lars on 2008-02-27
Have you restarted since you removed Ekiga?

---

### Post by arashiko28 on 2008-02-27
yes I did, and then tried to see if my mouse worked again, didn't and the thing went mad again. It does not respond to the kill command, nor killall, nor kill -9, nothing! It's driving me mad!

---

### Post by Sam Lars on 2008-02-27
Looks like you're not alone, I found a few other threads on this.
If you do
```
/etc/init.d/udev restart
```
Does it stop?

From [here]("http://ubuntuforums.org/showthread.php?t=580170") I got this fix:
```
sudo modprobe -r ehci_hcd
```
They said it was from here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware#Workaround_for_random_device_disconnections](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware#Workaround_for_random_device_disconnections)

Any of that work for you?

---

### Post by arashiko28 on 2008-02-27
Actually I didn't tried it. I disconnected all the peripherals and made a normal restart that took about 15 minutes, when it came back up, everything was ok, my mouse works, my pc fly everything is back to normal. Thanks anyway, that might be of use to others, took me too long to find the solution.

---

