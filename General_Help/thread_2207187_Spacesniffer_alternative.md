---
title: "Spacesniffer alternative?"
date: 2014-02-22
forum: General Help
---

### Post by pendulous on 2014-02-22
Anyone know of an alternative similar to SpaceSniffer for Windows, and a better alternative to Ubuntu's Disk Usage Analyzer? 

Disk Usage Analyzer is fairly useless, imo, and pulls information from every drive on the system. Instead of letting the user select the media to analyze, not only the graphs are horrible and layout is just unintuitive.

 I need to find out how I achieved 55GB of data in just a few days after installing Ubuntu and only a few programs added. I've ran cleanups posted [here]("http://ubuntuforums.org/showthread.php?t=140920"), but hasn't helped any

---

### Post by Impavidus on 2014-02-22
I agree that disk space analyser isn't very useful. This thread gives some ideas to analyse disk space usage: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

My first guess would be overflowing log files.

---

### Post by Morbius1 on 2014-02-22
JDiskReport?

[http://www.jgoodies.com/downloads/jdiskreport/](http://www.jgoodies.com/downloads/jdiskreport/)

---

### Post by pendulous on 2014-02-22
yeah, seems like log reports and this directory named 1 .... the link I posted on cleanup ought to have taken care of the log files. What other methods can be used?

[IMG]http://oi60.tinypic.com/257de90.jpg[/IMG]

---

### Post by coldcritter64 on 2014-02-23
Some info for log clearing, look for the .gz files for removal, [http://askubuntu.com/questions/100004/how-can-i-free-space-from-a-massive-39-5gb-var-log-folder](http://askubuntu.com/questions/100004/how-can-i-free-space-from-a-massive-39-5gb-var-log-folder)

---

### Post by Impavidus on 2014-02-23
Have a look at the log files, look for any repeating messages. These can give a clue for solving your problem.

---

### Post by pendulous on 2014-02-23
Ok, this is ridicilous! These utilities are useless. I've litterally looked at the properties of each folder/file size and I now have 700mb of free space left and the system is warning. 

Jdisk and Ubuntu's disk analyzer do not display 'individual' folder sizes, only the root directory folder size, sorry but no links provided were of use. Hastily created apps, not reliable at all.

providing the following:
```
root@TEST:/# du -sk * | sort -n
45327824    log
```

What I discovered is bandwidth (1.2GB), kern.log (22.6 GB), syslog (7.8 GB), and syslog.1 (14.8 GB). This is where the 46.4 GB of arbitrary data is located.

One would think developers would put into place cleaning utilities for these in system settings, such as how the user want's to record logs (verbose, size, error reporting, etc..). Also, a 'system reboot,' as claimed clears the logs, sure whatever -- did that twice, among a plathora of other useless utilities, commands and suggestions.

Clean: this is the FIX
```

su
> /var/log/kern.log
> /var/log/bandwidth
> /var/log/syslog
> /var/log/syslog.1
```



What I would like to know... how can someone execute these commands once the logs reach a certain file size?

---

### Post by Morbius1 on 2014-02-23
Your log files are enormous. Here's what JDiskReports shows as the largest in my system:
[ATTACH=CONFIG]250607[/ATTACH]

---

### Post by pendulous on 2014-02-23
> **Morbius1 said:**
> Your log files are enormous. Here's what JDiskReports shows as the largest in my system:
[ATTACH=CONFIG]250607[/ATTACH]


Right, when I used jdisk and ubuntus tool it reflected those files as 4096kb... nothing was above, but selecting the root /var shown a larger value.

---

### Post by cplus-pasion on 2014-08-13
Hi,

I tried the **jDiskReport **and it's quite **bad**.
Intuitively, I clicked or right-clicked the files I wanted to remove / delete and it didn't let me. So... what should I do? Should I navigate to that path, for each file? That is ridiculous.

The good thing is that **SpaceSniffer ****works OK with Wine**. So, I mounted all my Windows drive under the /media/ folder and mount it again in Wine.
I started the spacesniffer.exe and give it a try. 

[COLOR=#008000]SpaceSniffer [/COLOR]with **[COLOR=#008000]Wine[/COLOR]** is definetly **slower **and the disk "**real-time**" changes are basically **non-existent**, but the program works and you can do your job... manually updating the drive map :)

So... give it a try.

---

