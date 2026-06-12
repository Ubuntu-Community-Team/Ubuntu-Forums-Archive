---
title: "If bash script executes command, &amp; killall kills bash script, is command killed, too?"
date: 2020-07-30
forum: General Help
---

### Post by raphaell2 on 2020-07-30
If I have a terminal open, and in it, a bash script I've made is running, and that bash script executes a specific command line command, and that takes a while; and if, during that time, in a different terminal, I use killall to kill the bash script in question - will killall then kill the command that my bash script was executing when I killed it, too?

---

### Post by TheFu on 2020-07-30
Yes.  Any running process in the process table will be matched based on the killall input.  Depending on what you really are trying to accomplish, there are probably better job control methods.

---

### Post by raphaell2 on 2020-07-30
Thank you!

---

### Post by TheFu on 2020-07-30
> **raphaell2 said:**
> Thank you!

Looks like I was wrong ... for certain cases.

You should test this yourself.  Just create a bash script that sleeps for 10 minutes.
```
#!/bin/bash
echo "Starting $0"
sleep 10m
echo "Stopping $0"

```

Name it "waste-10-minutes"; chmod +x waste-10-minutes
Run it twice - or 20 times.  Doesn't matter. Here's a command to do that with a 2 second delay between each
```
for N in {1..20} 
do 
  ./waste-10-minutes &
  sleep 2s
done
```

Check they are all running ...
```
$ jobs
[1]   Running                 ./waste-10-minutes &
[2]   Running                 ./waste-10-minutes &
[3]   Running                 ./waste-10-minutes &
[4]   Running                 ./waste-10-minutes &
[5]   Running                 ./waste-10-minutes &
[6]   Running                 ./waste-10-minutes &
[7]   Running                 ./waste-10-minutes &
[8]   Running                 ./waste-10-minutes &
[9]   Running                 ./waste-10-minutes &
[10]   Running                 ./waste-10-minutes &
[11]   Running                 ./waste-10-minutes &
[12]   Running                 ./waste-10-minutes &
[13]   Running                 ./waste-10-minutes &
[14]   Running                 ./waste-10-minutes &
[15]   Running                 ./waste-10-minutes &
[16]   Running                 ./waste-10-minutes &
[17]   Running                 ./waste-10-minutes &
[18]   Running                 ./waste-10-minutes &
[19]-  Running                 ./waste-10-minutes &
[20]+  Running                 ./waste-10-minutes &
$ 

```

And the sleep is running too:
```
$ psg sleep
thefu       10430 10428  0 16:00 pts/2    00:00:00 sleep 10m
thefu       10434 10432  0 16:00 pts/2    00:00:00 sleep 10m
thefu       10439 10437  0 16:00 pts/2    00:00:00 sleep 10m
thefu       10444 10442  0 16:00 pts/2    00:00:00 sleep 10m
thefu       10447 10445  0 16:00 pts/2    00:00:00 sleep 10m
thefu       10450 10448  0 16:00 pts/2    00:00:00 sleep 10m
thefu       10454 10452  0 16:00 pts/2    00:00:00 sleep 10m
thefu       10457 10455  0 16:00 pts/2    00:00:00 sleep 10m
thefu       10463 10461  0 16:00 pts/2    00:00:00 sleep 10m
thefu       10466 10464  0 16:00 pts/2    00:00:00 sleep 10m
thefu       10472 10470  0 16:00 pts/2    00:00:00 sleep 10m
thefu       10476 10474  0 16:00 pts/2    00:00:00 sleep 10m
thefu       10479 10477  0 16:00 pts/2    00:00:00 sleep 10m
thefu       10483 10481  0 16:00 pts/2    00:00:00 sleep 10m
thefu       10486 10484  0 16:00 pts/2    00:00:00 sleep 10m
thefu       10489 10487  0 16:01 pts/2    00:00:00 sleep 10m
thefu       10493 10491  0 16:01 pts/2    00:00:00 sleep 10m
thefu       10498 10496  0 16:01 pts/2    00:00:00 sleep 10m
thefu       10503 10501  0 16:01 pts/2    00:00:00 sleep 10m
thefu       10506 10504  0 16:01 pts/2    00:00:00 sleep 10m
thefu       10625 31843  0 16:02 pts/2    00:00:00 grep sleep
```

Now ... killall 
```
killall waste-10-minutes
```

Ok - that did kill all the waste-10-minutes scripts, but didn't kill the sleeps. When the parent process dies/gets killed, all the child processes get killed too. Is there something about "sleep" that's different?  Nope.  It was because the parent was detached using "job control".  If you don't do that, then it will work as stated.  

I routinely push long running tasks onto different queues.  The point is to have those tasks run in order, let them fully utilize the compute resources one at a time, but make adding more jobs to the queue easy.  I use TaskSpooler for this - it is in the repos.  A linux.com article about it: [https://www.linux.com/news/queuing-tasks-batch-execution-task-spooler/](https://www.linux.com/news/queuing-tasks-batch-execution-task-spooler/)  The command for the repo version isn't ts, it is **tsp**.  Before I found taskspooler, I was either writing tiny scripts or scheduling jobs in the future using 'at'.  It was a pain and sometimes the systems would be idle for hours because I'd make a guestamate wrong or worse - somethings multiple heavy programs would overlap.  [https://www.youtube.com/watch?v=wv8D8wT20ZY](https://www.youtube.com/watch?v=wv8D8wT20ZY) if you prefer a video guide.
tsp supports different queues, writes the CLI output to files in /tmp/ so if file permissions allow, other people can watch the progress.  tsp has job control to let you kill or reorder tasks.  Pretty handy.  The video says it isn't in the repos - that's an old video, but still good enough. It has been in Ubuntu's repos for a while.

If you have lots of commands like I did that were going to waste 10 minutes and you want to kill them ... I wasn't willing to kill all "sleep" commands, since some remote access programs use sleep between their monitoring for how connections are working. It would be bad to kill those tasks.  Anyways - learn to use a little awk to pull the PID from the process table (with specific grep restrictions) that can be fed into the normal kill command.  A ps command + grep ...
```
alias psg='ps -eaf | grep $*'
```

And that awk ...
```
$ psg sleep | awk '{print $2}' | xargs echo kill
kill 4222 4403 7207 7208 7209 7210 11984
```

I'd killed a few sleeps before getting bored.  Some people might make a bashrc function "slay {}" ... 

Anyways, lots of options for us shell users. ;)

---

