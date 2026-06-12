---
title: "CPU's are stuck at 100% because ofCPUminer please help"
date: 2014-01-13
forum: General Help
---

### Post by RiotsHere on 2014-01-13
Yeah, I was running cpuminer for a while my system crashed and I was getting errors when trying to login so I just reinstalled the OS but CPUminer 2.3.2 settings are still on the CPU's so they are running at 100% lol anyone know how to kill or set it back to default  because nothing is on the computer and its really laggy and hard to install things

---

### Post by baabsaget on 2014-01-13
When you log into your computer, go into a terminal (ctrl-alt-T) and type the following commands (you'll need your password)

sudo killall cpuminer

if that does not work:

ps -ax | grep cpuminer

sudo kill *all the numbers of processes with cpuminer in the name*

---

### Post by RiotsHere on 2014-01-13
first command I got no process found

I got this for ps -ax | grep cpuminer

warning: bad ps syntax, perhaps a bogus '-'?
See [http://gitorious.org/procps/procps/blobs/master/Documentation/FAQ](http://gitorious.org/procps/procps/blobs/master/Documentation/FAQ)
 5782 pts/0    S+     0:00 grep --color=auto cpuminer

Should I try and reinstall cpuminer then try it idk if I will be able to.

---

### Post by RiotsHere on 2014-01-13
is there anyway to defaut my init.d file or over write it with the one on my usb install for ubuntu?

---

### Post by deadflowr on 2014-01-13
It's in init.d?
What's the filename in the init.d folder.
Try
```
sudo /etc/init.d/<put-the-file-name-here> stop
```
or try this for 13.10
```
sudo stop <put-the-file-name-here> 
```
or this for 12.04
```
sudo service <put-the-file-name-here> stop
```
replace <put file name here> with the name of the file.
I don't how you'd disable it during boot/start up, so to do so, you could probably move the file somewhere else.

---

### Post by RiotsHere on 2014-01-13
Well, I did a reinstall of the OS because I couldn't log back on. so now all the files are gone and the settings are still in place just checked init.d just in case and everything is gone.

---

### Post by RiotsHere on 2014-01-13
Just check my system monitor and compiz is the name of whats running the CPU's so high you can't really kill that process ya know what I mean lol

I could be wrong but I think thats whats doing it idk would like to fix this but I'm thinking I will just have to boot from USB for a while

---

### Post by deadflowr on 2014-01-13
> **RiotsHere said:**
> Just check my system monitor and compiz is the name of whats running the CPU's so high you can't really kill that process ya know what I mean lol

I could be wrong but I think thats whats doing it idk would like to fix this but I'm thinking I will just have to boot from USB for a while

Compiz running heavy is usually a gpu thing.
Which is probably something that would need to be addressed in a separate thread. 

People better suited to answer how to fix that issue won't be reading a thread about cpuminer.

But for what it's worth, if you start a separate thread on the compiz issue maybe start out by posting the results of this command
```
sudo lshw -C display
```
that'll give the graphics card and the driver in use, which should help others figure out what needs to be done, if anything can done. 
Maybe link this thread as well, to give a full idea of how you found the problem.
The more people know the better results they can give.

---

### Post by RiotsHere on 2014-01-13
I had hooked up the computer I was mining with to my tv so I could watch it from my desktop, when it crashed and I got errors I couldn't find any info on. I then reinstalled the OS. The computer was still connected to the TV I assume it set up based on that TV resolution or something. its fixed now, thank you very much for all the good ideas!

---

