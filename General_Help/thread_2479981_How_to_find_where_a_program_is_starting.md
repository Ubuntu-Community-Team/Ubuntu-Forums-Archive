---
title: "How to find where a program is starting?"
date: 2022-10-14
forum: General Help
---

### Post by stevermann on 2022-10-14
I have a program, duplicity, that is making backups to a thumbdrive. But it won't stop.  It's always running.

```
ps -aux | grep duplicity
steve    19047  0.0  0.0  14428  1044 pts/0    S+   16:08   0:00 grep --color=auto duplicity



```

How can I find how it was started?  
It doesn't appear in *systemctl -a, *nor is there anything in crontab, so how can I find how duplicity is starting?

---

### Post by #&amp;thj^% on 2022-10-14
That Looks at first glance normal IE:
```
ps -aux | grep duplicity 
me        330878  0.0  0.0   6568  2580 pts/0    S+   14:13   0:00 grep duplicity


```
And No cronjob...
```
ps ax | grep rsync
 340926 pts/0    S+     0:00 grep rsync



```
"killall rsync" will stop all running rsync processes.
If you have more rsyncs running in parallel and want to stop just one of them: "kill [process_ID]". You can get the process_ID from ps ax (it's the first column).
man duplicity: [https://linux.die.net/man/1/duplicity](https://linux.die.net/man/1/duplicity)

---

### Post by TheFu on 2022-10-14
> **stevermann said:**
> I have a program, duplicity, that is making backups to a thumbdrive. But it won't stop.  It's always running.

```
ps -aux | grep duplicity
steve    19047  0.0  0.0  14428  1044 pts/0    S+   16:08   0:00 grep --color=auto duplicity



```

How can I find how it was started?  
It doesn't appear in *systemctl -a, *nor is there anything in crontab, so how can I find how duplicity is starting?

That isn't duplicity running. It your grep command looking for duplicity.

I have an alias ... 
```
alias psg='ps -eaf | grep $*'
```
There's also 'pgrep -a {pattern}'.  I'm lazy and don't want to type more than 3 character commands. ;)

---

### Post by Holger_Gehrke on 2022-10-14
Look closer. That's not duplicity running, it's your grep searching for 'duplicity'. To make it so that grep doesn't find itself in a process list, you have to be a bit more tricky.
```

ps -aux | grep '[d]uplicity'

```
The regular expression '[d]uplicity' can only evaluate to 'duplicity' but is not identical to it, so grep won't output itself as a match. Alternatively you could use 'pgrep' instead of the ps-grep-pipeline.

Holger

---

### Post by stevermann on 2022-10-14
OK, thanks for that.
That doesn't answer the question- what is running duplicity occasionally?
I don't use it often, so I could just remove it and see what crashes?

---

### Post by TheFu on 2022-10-14
> **stevermann said:**
> OK, thanks for that.
That doesn't answer the question- what is running duplicity occasionally?
I don't use it often, so I could just remove it and see what crashes?

I think you've missed the key point.

**duplicity isn't running.**  The ps command used isn't finding a duplicity process, it is finding a grep process that is searching for duplicity.


As for determining what is starting a program, there are many, many, many, ways.  If I didn't already know the answer and quick searched of the 6 crontab locations, all the systemd locations, all the init.d/ programs and my 'at', 'batch' or 'taskspooler' queues  found nothing, there is a 'pstree' tool that shows which process is the parent of the one being asked about.  I bet there are 10 other, similar tools.  Heck, 'ps' shows the PID for the parent process, so you could use that to manually trace back, if you wanted.

```
$ pstree thefu
 xterm&#9472;&#9472;&#9472;bash&#9472;&#9516;&#9472;caja&#9472;&#9472;&#9472;4*[{caja}]
             &#9500;&#9472;losslesscut&#9472;&#9516;&#9472;losslesscut&#9472;&#9472;&#9472;losslesscut&#9472;&#9472;&#9472;losslesscut&#9472;&#9472;&#9472;11*[{losslessc+
             &#9474;             &#9500;&#9472;losslesscut&#9472;&#9516;&#9472;losslesscut
             &#9474;             &#9474;             &#9492;&#9472;7*[{losslesscut}]
             &#9474;             &#9500;&#9472;losslesscut&#9472;&#9472;&#9472;4*[{losslesscut}]
             &#9474;             &#9500;&#9472;losslesscut&#9472;&#9472;&#9472;17*[{losslesscut}]
             &#9474;             &#9492;&#9472;24*[{losslesscut}]
             &#9492;&#9472;xterm&#9472;&#9472;&#9472;ssh

firejail&#9472;&#9472;&#9472;firejail&#9472;&#9472;&#9472;firefox&#9472;&#9516;&#9472;Isolated Web Co&#9472;&#9472;&#9472;29*[{Isolated Web Co}]
                              &#9500;&#9472;9*[Isolated Web Co&#9472;&#9472;&#9472;26*[{Isolated Web Co}]]
                              &#9500;&#9472;13*[Isolated Web Co&#9472;&#9472;&#9472;27*[{Isolated Web Co}]]
                              &#9500;&#9472;Isolated Web Co&#9472;&#9472;&#9472;30*[{Isolated Web Co}]
                              &#9500;&#9472;Isolated Web Co&#9472;&#9472;&#9472;28*[{Isolated Web Co}]
                              &#9500;&#9472;Privileged Cont&#9472;&#9472;&#9472;27*[{Privileged Cont}]
                              &#9500;&#9472;RDD Process&#9472;&#9472;&#9472;2*[{RDD Process}]
                              &#9500;&#9472;Socket Process&#9472;&#9472;&#9472;5*[{Socket Process}]
                              &#9500;&#9472;Utility Process&#9472;&#9472;&#9472;2*[{Utility Process}]
                              &#9500;&#9472;3*[Web Content&#9472;&#9472;&#9472;18*[{Web Content}]]
                              &#9500;&#9472;WebExtensions&#9472;&#9472;&#9472;29*[{WebExtensions}]
                              &#9492;&#9472;169*[{firefox}]

fvwm2&#9472;&#9516;&#9472;FvwmAnimate
      &#9500;&#9472;FvwmButtons
      &#9500;&#9472;FvwmIconMan
      &#9500;&#9472;2*[FvwmPager]
      &#9500;&#9472;alarm-clock-app&#9472;&#9472;&#9472;2*[{alarm-clock-app}]
      &#9500;&#9472;firefox.sh
      &#9500;&#9472;ssh-agent
      &#9500;&#9472;thunderbird.sh
      &#9500;&#9472;xclock
      &#9500;&#9472;xload
      &#9500;&#9472;xscreensaver
      &#9492;&#9472;xterm&#9472;&#9472;&#9472;bash&#9472;&#9472;&#9472;ghb&#9472;&#9472;&#9472;53*[{ghb}]

xterm&#9472;&#9472;&#9472;bash&#9472;&#9472;&#9472;pstree

xterm&#9472;&#9472;&#9472;bash

xterm&#9472;&#9472;&#9472;ssh

xterm&#9472;&#9472;&#9472;ssh

xterm&#9472;&#9472;&#9472;ssh
....
```
There are lots of options for pstree. The manpage documents those.

---

### Post by stevermann on 2022-10-14
Thanks for that. I hadn't heard of pstree before.

---

### Post by mIk3_08 on 2022-10-15
> **stevermann said:**
> I have a program, duplicity, that is making backups to a thumbdrive. But it won't stop.  It's always running.
How can I find how it was started?  
It doesn't appear in *systemctl -a, *nor is there anything in crontab, so how can I find how duplicity is starting?
Program really starts at startup application. and you can see it running at system monitor or you can just type the command below in your terminal. Regards and cheers
```
ps -e
```

---

