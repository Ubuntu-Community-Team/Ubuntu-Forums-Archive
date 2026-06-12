---
title: "[SOLVED] Do Linux programs take advantage of Dual Cores?"
date: 2007-08-17
forum: General Help
---

### Post by sci-fi guy on 2007-08-17
Just what it says. Can Ubuntu use both cores fully? Even if running a single program?

---

### Post by fjgaude on 2007-08-17
Linux recognizes, uses two or more Cores, CPUs, but it depends on the program. If it is threaded more than one core will be used. Linux is very efficient with multiple CPUs, running multiple programs in parallel.

frank

---

### Post by HermanAB on 2007-08-17
See these puppies:
[http://www.top500.org/](http://www.top500.org/)

Of the top 500, about 300 run Linux and the rest run other flavours of Unix, with only *one* running MS Windows.

---

### Post by pmg on 2007-08-17
As long as you're running an SMP kernel.  Run **uname -v** and see if is includes the string **SMP**.  Hmm, I just realized it's running the SMP kernel on my uni-system.  No harm in that.  It's probably doing a little extra work that wouldn't be necessary on a single processor system.  Hmm, does feisty *always* install SMP kernels?

---

### Post by Motoxrdude on 2007-08-17
No. Linux can't make single threads utilize both cores. It is entirely up to the program whether it utilizes both cores (it has to be multi-threaded), but linux can optimize a single threaded program by running it on one core and dumping everything else on the other if it is a process intensive program.

---

### Post by sci-fi guy on 2007-08-18
Can multi-threaded programs run on a single core? (just out of curiosity)

---

### Post by pmg on 2007-08-18
> **sci-fi guy said:**
> Can multi-threaded programs run on a single core? (just out of curiosity)
Yes, that happens all the time.  They are dispatched similar to multiple processes (like your applications running at the same time as the Xserver, and your display manager, and all the rest of the system.)  All you'll see is that things will run slower (than having multiple processors.  I should really say *might* run slower, because in some cases you won't even noticed the performance difference.)

---

### Post by statictonic on 2007-08-18
I watched CPU usage while using the computer, and it seemed to be pretty well split overall on what core is being used, so I would say that plenty of programs do, I'm not sure how exactly it is setup though.

---

