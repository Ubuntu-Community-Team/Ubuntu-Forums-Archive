---
title: "Using &quot;time&quot; to assess browser start-up time"
date: 2013-05-18
forum: General Help
---

### Post by vasa1 on 2013-05-18
There are two posts employing "time" to assess how quickly a browser opens:
[http://ubuntuforums.org/showthread.php?t=2145873&p=12652799#post12652799](http://ubuntuforums.org/showthread.php?t=2145873&p=12652799#post12652799)
and
[http://ubuntuforums.org/showthread.php?t=2145873&p=12653224#post12653224](http://ubuntuforums.org/showthread.php?t=2145873&p=12653224#post12653224)

The commands look like this:
```
time firefox
```and
```
time chromium-browser
```
My confusion is this:
The results of time will appear **only after** the browser window is closed. 
[FONT=Courier New]**man time**[/FONT] has this:> The time command returns when the program exits, stops, or is terminated by a signal.
Assuming **time** is otherwise perfect, there's a chance of human error in terms of **how efficient we are** in closing the browser.  
So is there any means to chain some sort of "exit browser" command to eliminate the chance of human error?
"Kill" needs to know the process/job ID.

Ideally, is there a way to measure how quickly any graphical application, not just a browser, opens?

---

### Post by CaptainMark on 2013-05-19
The output of time gives three things:
real time (total running time)
user time (time cpu spent processing code in user space)
sys time (time cpu spent processing code at kernel level)

So adding up user + sys will give you total time that the cpu was working on the application for. I think its the closest that youll get to working out the uptime, by default this would include time taken for the cpu to close the application too but if you use this method but manually cut the process off from the same terminal you ran the initial time command in (using ctrl+c) you should get a reasonably accurate result of how long the cpu spent opening the application.

---

