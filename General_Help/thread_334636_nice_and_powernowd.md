---
title: "nice and powernowd"
date: 2007-01-09
forum: General Help
---

### Post by jeremytaylor on 2007-01-09
Hi, 
I'm using ubuntu on my laptop and in the past I have niced processes as the default behaviour or powernowd is to ignore these in the cpu scaling and so I can run long jobs without melting my machine.
However since I switched to edgy this behaviour doesn't seem to hold. Even well niced processes tend to switch the cpu up to its max frequency. If I start the powernowd deamon again from the command line then the behaviour goes back to what I expect.

Does anyone know how I can force it to start with the write behaviour without having to start it again manually?

many thanks
Jeremy

---

### Post by teaker1s on 2007-01-09
you could write a little script that made sure that powernowd was running and if not restart using possibly update-rc.d  to control run levels

[http://www.penguin-soft.com/penguin/man/8/update-rc.d.html]("http://www.penguin-soft.com/penguin/man/8/update-rc.d.html")

---

### Post by jeremytaylor on 2007-01-09
Okay, thanks. I'm pretty sure powernowd is running as the processor does change frequency, according to demand... the problem is that it is not ignoring niced tasks.

thanks again
Jeremy

---

### Post by RandomJoe on 2007-01-09
There is a switch for powernowd to include 'niced' programs (-n) - is Edgy using that switch by default?  I just checked mine (6.06) and it doesn't.

If it does have that switch, just find the command that gets started in /etc/init.d and remove the -n.

---

### Post by jeremytaylor on 2007-01-10
mine has no -n either.
Hmmm, curious. Thanks for the suggestion though!
Jeremy

---

### Post by TheKiteGuy on 2007-03-12
I've just been looking at the same problem.

In /etc/init.d/powernowd, the powernowd is only started if use_ondemand is false. From what I've read, the kernel now has built into it it's own power management functionality, so the startup script isn't bothering launching powernowd if it can use that instead.

There are two ways of easily doing what you want to do: 
Either comment out the five lines in /etc/init.d/powernowd at approximately line 109 between if use_ondemand and fi inclusive by placing a # symbol at the start of each. 
This will make powernowd will run anyway (which seems to work OK for me), or you can enter:

   	    echo -n "1" >$x/cpufreq/ondemand/ignore_nice_load;
before the done line (line 89) in the use_ondemand function in the same file. This will tell the kernel power manager not to include nice programs in the calculation when dynamically varying the processor load to match demand. 

Both ways seem to work for me. I need to restart my pc several times to check though.

Hope this helps!

---

### Post by jeremytaylor on 2007-03-13
That works. Brilliant, thank you!
Jeremy

---

