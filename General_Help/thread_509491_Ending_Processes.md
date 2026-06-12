---
title: "Ending Processes"
date: 2007-07-25
forum: General Help
---

### Post by jg0149 on 2007-07-25
I tried to install vmware with adept manager.  The bar went to 34% and stopped, for a couple of hours (I was doing some other stuff).  I closed the window and tried to open another package installer.  I got an error telling me a system was in use and I need to close it.  How the heck do I do taht?  I looked through some documentaion on kdsys...

---

### Post by Seisen on 2007-07-25
Try

```
sudo kill
``` to kill the process press the **K** key then put in the process number.

---

### Post by Nekiruhs on 2007-07-25
> **Seisen said:**
> Try

```
sudo kill
``` to kill the process press the **K** key then put in the process number.
You do mean top not kill right? Sudo kill brings up a usage error. 
```
sudo top
```
then press k and type the Process #.

---

### Post by Majorix on 2007-07-25
You can end processes using a GUI called System monitor. Its under System > Admin. Click and kill, easy right? :)

---

### Post by jg0149 on 2007-07-25
How do I find out the process number????

---

### Post by Seisen on 2007-07-25
> **Nekiruhs said:**
> You do mean top not kill right? Sudo kill brings up a usage error. 
```
sudo top
```
then press k and type the Process #.

Yes I don't know why I put kill their.

> How do I find out the process number????

Its the PID number

```
22281 michael   39  19 18388 8168  896 R 93.5  1.8 163:19.84 FahCore_78.exe  
```

For example the process number for Folding@home is 22281 on my computer.

> You can end processes using a GUI called System monitor. Its under System > Admin. Click and kill, easy right?

Unfortunately not everything shows up in system monitor.

---

### Post by jg0149 on 2007-07-25
When I use the GUI, and kill, I get an error that I don't have sufficient permissions.  The thing is I am the administrator for the computer, I should be able to do anything.

I tried sudo kill and then k (PID number) and can't kill the process yet.  what now?

---

### Post by Seisen on 2007-07-25
Its supposed to be 

```
sudo top
``` somebody in a earlier post caught my mistake.

---

### Post by jg0149 on 2007-07-25
I type in sudo top and get a list.  The list is not the same as the GUI adept manager and the sudo list doesn't show the process I need to end.    The process I need to end shows the login as root.  How do I login as root?

---

### Post by MrHippocampus on 2007-07-25
A nice fun way to kill a program is to open up a terminal and type in xkill (should be installed by default). The mouse cursor will change to a skull and crossbones, now if you click on a window the process which spawned that window will be killed :)

edit: if you want this to work as root just try "sudo xkill"

---

### Post by Seisen on 2007-07-25
> **jg0149 said:**
> I type in sudo top and get a list.  The list is not the same as the GUI adept manager and the sudo list doesn't show the process I need to end.    The process I need to end shows the login as root.  How do I login as root?

Post what it says when you put ```
top
``` in the terminal.

---

### Post by jg0149 on 2007-07-25
I can't figure how to copy the screen.  I have 116 tasks, 3 running; 113 sleeping.  No processes stopped or Zombie.  CPU usage is near 50%.

I am still getting an error.  The system rebooted quickly because Mozilla Firefox seems to make the KDE desktop crash every so often.

---

### Post by Seisen on 2007-07-25
Just take your mouse and highlight the area you want to copy than one you select that area right click and then select copy.

---

### Post by jg0149 on 2007-07-25
I tried to copy and I highlight the Konsole screen.  I don't get a chance to copy because it updates and clears my highlight.  I printed tieh screen to a pdf file and when I put it in this box, it lost all formatting.  Is there a way I can close the process from a command line?

---

### Post by jg0149 on 2007-07-25
top - 15:44:46 up  7:41,  1 user,  load average: 5.55, 4.97, 4.19
Tasks: 100 total,   5 running,  95 sleeping,   0 stopped,   0 zombie
Cpu(s): 67.0%us, 32.3%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.7%hi,  0.0%si,  0.0%st
Mem:    514956k total,   384196k used,   130760k free,    12444k buffers
Swap:  1502036k total,    34116k used,  1467920k free,   183916k cached

---

### Post by Seisen on 2007-07-25
You need post at least the first few processes.

---

### Post by Majorix on 2007-07-25
Well if gnome-system-monitor doesn't work for you you can try gps.

```
sudo apt-get install gps
```

Then you can start it with root privileges as follows

```
sudo gps
```

I like it the visual way 8-)

---

### Post by jg0149 on 2007-07-25
I shut down the computer to close all processes and restarted.  I still have a process open and can't figure out which one I need to close.

I did copy the running processes:

top - 17:05:38 up 16 min,  1 user,  load average: 4.16, 2.90, 1.64
Tasks: 107 total,   3 running, 103 sleeping,   0 stopped,   1 zombie
Cpu(s): 64.1%us, 15.0%sy,  0.3%ni, 20.3%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    514956k total,   505208k used,     9748k free,   120060k buffers
Swap:  1502036k total,    31740k used,  1470296k free,   190160k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6277 jeff      15   0 34212  14m  10m S 56.2  2.8   4:54.46 gnome-system-mo
 5490 root      15   0 84324  12m 4336 R 10.9  2.4   0:58.41 Xorg
 6308 jeff      15   0  165m  45m  21m R  5.0  9.1   1:16.33 firefox-bin
 6362 jeff      15   0 32176  14m  11m S  4.6  2.9   0:04.65 konsole
 6424 jeff      37  12 56344  16m 8308 S  1.0  3.2   0:09.62 beagled-helper
 6380 root      15   0  2316 1156  880 R  0.7  0.2   0:01.89 top
 6438 root      15   0 34000  11m 9568 S  0.3  2.4   0:00.36 knotify
    1 root      18   0  2908 1848  524 S  0.0  0.4   0:03.19 init

---

### Post by jocko on 2007-07-25
If I've understood you correctly, your package manager got stuck during an installation, and now you get an error message claiming that the apt system is already in use, even after a reboot?
This may be caused by an interrupted installation.
In that case the problem can perhaps be solved by running this in a terminal:
```
sudo dpkg --configure -a
```Another problem could be that the package manager was not shut down properly, which could have left the apt system locked. In this case this may help:
```
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/apt/lists/lock
sudo rm /var/lib/dpkg/lock
sudo aptitude update
```

---

### Post by NorthernSuze on 2007-07-26
> A nice fun way to kill a program is to open up a terminal and type in xkill (should be installed by default). The mouse cursor will change to a skull and crossbones, now if you click on a window the process which spawned that window will be killed 
@MrHippocampus:  oh, the xkill just made my day  :lolflag:  "Prepare to die, Earth scum" click, click, click <grin>

> Another problem could be that the package manager was not shut down properly, which could have left the apt system locked. In this case this may help:
Code:
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/apt/lists/lock
sudo rm /var/lib/dpkg/lock
sudo aptitude update
@Jocko:  Thank-you for timely commands for a problem I was only dimly becoming aware of!  You guys are amazing.

---

### Post by qpieus on 2007-07-26
xkill can also be invoked by pressing ctrl-alt-esc

---

### Post by qpieus on 2007-07-26
> **jg0149 said:**
> How do I find out the process number????
already mentioned was the top command. 
Instead of top, try htop (it's in the repos). htop is top on steroids.

```
ps aux
```

also gives you process information

---

