---
title: "Resume a process on a different tty?"
date: 2008-02-19
forum: General Help
---

### Post by dimmer on 2008-02-19
I guess my question applies to jobs in general. I have sometimes started a long process, only to wish  later I had started it in screen instead. I want to be able to pause the job and resume it in screen, instead of stopping it and starting it over again in screen.

To stop a job you hit ctrl+z.  Then to run it in the background you hit "bg". Sometimes this doesn't always work though, and I'm not sure why. For example with this little test case:

```

mkdir /tmp/delme
for n in `seq 1 10000`; do touch /tmp/delme/$n; done;

```

If you hit ctrl+z quickly after running this, you will stop new files from being created. fg or bg will not resume this job. I guess it depends on how the process handles the STOP signal?

Well, even if this process could be resumed (like say, 'top', can), when you type "screen" and then "fg" you get:
```
-bash: fg: current: no such job
```

Annoyingly, my ubuntu system doesn't have man pages for fg,bg, or jobs.

I have STW (although not exhaustively, yet) - I'm hoping there is a shell guru out there who has the answer?

---

### Post by pointone on 2008-02-19
The correct usage is "fg [job_id]". Use ps to find the pid of the process, then run fg with that number.

---

### Post by dimmer on 2008-02-19
> **pointone said:**
> The correct usage is "fg [job_id]". Use ps to find the pid of the process, then run fg with that number.

arguments are optional. If you don't type any arguments it tries to load the first job.
[http://www.research.att.com/~gsf/man/man1/fg.html]("http://www.research.att.com/~gsf/man/man1/fg.html")

---

### Post by pointone on 2008-02-19
Yes, I know. I suggested that in case another job was being "found" as the "most recently suspended" (not the first) job.

However, I just tested that script on my laptop and it works fine with fg/bg. This is running Arch Linux from the command line.

Try running it from an actual console rather than gnome-terminal or konsole, etc.

*EDIT* Nevermind; it's not working between ttys. :(

---

### Post by dimmer on 2008-02-20
Thanks a lot for trying! You get an A for effort ;-)

---

### Post by lardbit on 2008-03-26
> **dimmer said:**
> 
Annoyingly, my ubuntu system doesn't have man pages for fg,bg, or jobs.


i don't know the answer to this thread, but you can do 
```
$help [name]
```

like 'help jobs' for instance.

---

### Post by getraktna on 2008-06-24
Can you also switch the tty to which the process is tied to?

---

