---
title: "Command for faster process?"
date: 2023-09-18
forum: General Help
---

### Post by SciGuy1872 on 2023-09-18
Hi.  I posted this to the Ubuntu Mate forum also.    I have the following command to turn *.jpg to *.dds for X-Plane


 ```
ls *.jpg | xargs -I TEX basename TEX .jpg | xargs --max-procs=4 -I TEX2 convert TEX2.jpg TEX2.dds
```

 
I was wondering if I can edit this command to make it faster?  The  webpage where this command comes from states that the "procs" controls  the number of parallel processes; I was wondering if I can increase this  for a faster conversion?  I have a quad-core i5 3.2GHz and an Nvidia  GTX 1650.

---

### Post by TheFu on 2023-09-18
> **SciGuy1872 said:**
> Hi.  I posted this to the Ubuntu Mate forum also.    I have the following command to turn *.jpg to *.dds for X-Plane


 ```
ls *.jpg | xargs -I TEX basename TEX .jpg | xargs --max-procs=4 -I TEX2 convert TEX2.jpg TEX2.dds
```

 
I was wondering if I can edit this command to make it faster?  The  webpage where this command comes from states that the "procs" controls  the number of parallel processes; I was wondering if I can increase this  for a faster conversion?  I have a quad-core i5 3.2GHz and an Nvidia  GTX 1650.

Using more processes than the CPU supports usually makes things slower, unless it is I/O bound.  Can't hurt to run a few tests, right?  Try 4, 6, 8 and use 'time'.  Convert (and all ImageMagick tools) are multithreaded, so you might get faster processing using the *-limit thread 1* option to convert. Play with different values for the number of threads. Many things are system-specific, so nobody without the exact same system can really tell you the best/fastest answer.  I'd run the same files thought thread limits with 1, 2, 4, 6, 8 to see how that works.

Using max-procs is only for xargs. It will control how many parallel processes (usually the number of 'convert' processes) will be run concurrently. The optimal value will be impacted by the threading for each individual convert job.

You can check if OpenMP is compiled into the ImageMagick tools you have by using the **--version** option. I checked 20.04 and 22.04 systems here. Both using default repos and OpenMP was enabled.

BTW, feeding the output from **ls** into any command is dangerous. Most of the time, it works, but when it fails, it fails badly and silently. If you need EVERY file to be processed, you'll want to ensure the list of files is provided in a different way.  bash can do file globbing, which will ensure the files you want are used.  I realize this is a subtle difference, but it does matter ... er ... when it matters.

---

### Post by SciGuy1872 on 2023-09-18
Hi.  Thanks for the answer.  Just to be sure, you're saying to try the command with the part about threading with 1,2,4,6,8 to try to find the best?  Where does "time" go?  This computer has 1 physical processor, 4 cores, 4 threads, if that info helps.  Would the *-limit thread 1* option be after -I (that "I" is an option, so I figured that would be an okay place)?

---

### Post by MAFoElffen on 2023-09-18
You could also test a value of "0":

RE: man xargs
```

       -P max-procs, --max-procs=max-procs
              Run  up  to  max-procs  processes at a time; the default is 1.  If max-procs is 0, xargs will run as
              many processes as possible at a time.  Use the -n option or the -L option with -P; otherwise chances
              are  that  only  one  exec will be done.  While xargs is running, you can send its process a SIGUSR1
              signal to increase the number of commands to run simultaneously, or a SIGUSR2 to decrease  the  num&#8208;
              ber.   You cannot increase it above an implementation-defined limit (which is shown with --show-lim&#8208;
              its).  You cannot decrease it below 1.  xargs never terminates its commands; when asked to decrease,
              it merely waits for more than one existing command to terminate before starting another.

              Please  note  that it is up to the called processes to properly manage parallel access to shared re&#8208;
              sources.  For example, if more than one of them tries to print to stdout, the output  will  be  pro&#8208;
              duced  in an indeterminate order (and very likely mixed up) unless the processes collaborate in some
              way to prevent this.  Using some kind of locking scheme is one way to  prevent  such  problems.   In
              general,  using  a  locking  scheme  will help ensure correct output but reduce performance.  If you
              don't want to tolerate the performance difference, simply arrange for each process to produce a sep&#8208;
              arate output file (or otherwise use separate resources).

```
Also a good read: [https://blog.tratif.com/2023/01/30/bash-tips-5-parallelism-using-xargs/](https://blog.tratif.com/2023/01/30/bash-tips-5-parallelism-using-xargs/)

---

