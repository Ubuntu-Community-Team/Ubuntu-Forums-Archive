---
title: "g++ and CPU processors problem (Ubuntu 12.04)"
date: 2013-06-19
forum: General Help
---

### Post by Sonke on 2013-06-19
This is my first post so I hope that I am in the right place and abide by the rules. Thank you for any help that you can give!

I am trying to run some C code using the g++ compiler. I typically run it as:
~$ g++ <filename>.cpp -o run_file
~$ ./run_file > output.log

The data that I am interested in is the time it takes a simulation to run, and I need to run many such programs. Rather than doing them all one after another I want to run several at the same time. 
I am pretty sure I have 8 processors, as confirmed by,
~$ cat /proc/cpuinfo
showing 8 seperate processor info summaries and,
~$ grep -c processor /proc/cpuinfo
saying "8".

I always thought that when I open a terminal, it roughly corresponds to working on one processor. Hence I tested how many programs I could get to run without them slowing each other down. I ran my .cpp file, it took about 220 seconds. Then I opened a second terminal and on both ran the same program, confirming that they both took the same time when rechecking the different log files (but they took slightly longer, 230s, than when running only one simulation). I continued up to about 6 terminals running 6 identical programs, but the times were decreasing already after running only 2 together. I expected that I will hit a barrier at about 6 programs, after which the OS and the 6 terminals may take up more than the 8 processors, but this seems not to be the case, instead it slows down far earlier.

After that, I ran some programs together in seperate terminals and (in a seperate terminal) used the "~$ top" command (with t and 1 pressed so that it displays individual processor info). I found that the work load often shifts between processors, despite all 8 never being fully utilised.. Ie, I would have a processor at 100% user used (the first column), and another at 0%. at the next refresh I had them both at about 50%, and the next refresh they were switched to 0% and 100% respectively. Could this be slowing down my simulations?

So my question is, how can I run programs together without them slowing each other down? Ideally, could I select, using g++ or otherwise, a specific processor to run a specific simulation, and ensuring that it only runs this simulation? That way I could control the workload much better and hopefully improve the accuraacy of my timing data. If this has been asked already, or is in the standard literature/documentation, I'm sorry for having missed it and would really appreciate any links! Also, less important but just out of curiosity, how does the workload get distributed across the processors? Is my one-terminal-one-processor assumption accurate in any way? How about the 'workspaces', are those just seperate canvases as it were, or do they effect the processor used?

"~$ g++ --version" gives "g++ (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3", if that makes any difference.
My computer is a Lenovo Y500 Ideapad laptop.

Thank you for your time and any advice!!

--
Sonke

---

### Post by Slim Odds on 2013-06-19
Take a look at GNU Parallel. It works like magic.

[https://www.gnu.org/software/parallel/](https://www.gnu.org/software/parallel/)

---

### Post by Impavidus on 2013-06-19
The processes may be competing for the bandwith to access RAM, hard disk etc. This also explains why they don't reach 100% CPU time. Depending on the type of your processors multiple cores may share the same cache, so running your process on both cores simultaniously causses more cache misses and slows the processes down.

When I look at the number of processors in my laptop (Intel i5 CPU) I get```
$ grep -c processor /proc/cpuinfo
4

```
There is one dual core processor in there, with part of the cache shared by both cores. They have hyperthreading, as Intel calls it, and therefore both cores are reported as 2 processors, yet it's only slightly faster than a normal core. Counting processors isn't always straight-forward.

---

### Post by Sonke on 2013-06-19
Dear Slim Odds,
Thank you for the suggestion! It took me a little while to get used to GNU (I'm pretty new to Linux! It was the first thing I've successfully installed through the terminal...), but I think I have it working correctly - but the problem remains! I ran a few trials, with 4, 5, and 6 simulations simultaneously running. And then checked the times, 6 was still the slowest, then 5 and 4 was the fastest. As in, the simulations were slowed down by having run more in parallel, despite my core limit (GNU says I have 8 available) not being reached. 
I used,
```
$ ls run_GNU_12cube_* | time parallel -j+0 --eta './{} > {}.log'
```
with 5 identical files: run_GNU_12cube_1 ... etc ... run_GNU_12cube_5. They all took about 250-300 seconds to complete (they varied much). Whilst when I ran
```
 $ ls run_GNU_12cube_* | parallel -j-7 --eta './{} > {}.log' 
``` 
changing the number of cores available to j-7=1 core only, ie the 5 simulations run in succession, I had that each of the codes took 217 seconds to run (+/- some milliseconds, barely any variation on their times). GNU is pretty convenient, but sadly the problem still remains!


Dear Impavidus,
Running the grep command you gave gives a value of 8, but after reading around on the net I think the chip is a quad-core with that hyperthreading giving it 8... is that a bad thing for scientific simulating?
I reran the GNU application with only 2 parallel simulations this time, hoping that a quad-core would mean that 2 cores will not suffer from the shared memory problem arising from the hyperthreading, but the problem still seems to be there. I had a simulation time of 225 and 229 seconds for them running in parallel. So I think that it might a different problem than running into hyperthreaded core sharing. If that is worded correcty. Admittedly I had firefox running (only typing this message though) whilst simulating the two core test, but I doubt it mattered. I will rerun it without firefox and edit if the times are normal! (EDIT: no firefox gives 224 seconds, still slightly high)

Are there any other suggestions for why simulations run in parallel are not as fast as those run solo when I have 4 cores (8 with hyperthreading)? I have 16GB of RAM, so there should not be any bottlenecking there, but aside from that I am not IT literate enough myself to know what else could be missing. But I think you are correct Impavidus, that there may be issues of resource sharing since the times with only 2 parallel simulations were much closer to the 217 seconds when running the code one at a time.

(apologies for any typos, holding a very spoilt baby as I typed...)

---

### Post by Slim Odds on 2013-06-19
Also, for monitoring CPU and Memory usage: htop

---

### Post by Slim Odds on 2013-06-19
There are always potential bottlenecks in parallel processing, like disk I/O.

Is there some resource that your parallel processes must share?

---

### Post by Impavidus on 2013-06-20
> **Slim Odds said:**
> There are always potential bottlenecks in parallel processing, like disk I/O.

Is there some resource that your parallel processes must share?

Always, I was thinking of [CPU cache]("http://en.wikipedia.org/wiki/CPU_cache"), which may be shared, or the [memory bus]("http://en.wikipedia.org/wiki/Memory_bus"). It takes time to access that memory.

Oh, you can take any hardware for scientific simulation, it may just take a little longer. I remember somebody telling me he had found a cardboard box filled with punch cards that were used for simulating the interior of stars. Those simulations took a while. By the clicking patterns of the relays they could hear what part of the code was being processed. Nowadays people put twenty nVidia cards together in a single Linux box to get a cheap supercomputer, really taking advantage of parallelism.

---

### Post by Slim Odds on 2013-06-20
> **Impavidus said:**
> Always, I was thinking of [CPU cache]("http://en.wikipedia.org/wiki/CPU_cache"), which may be shared, or the [memory bus]("http://en.wikipedia.org/wiki/Memory_bus"). It takes time to access that memory.<cut>
Any decent hardware design takes these things into account. If you use some cheap stuff (like the ones that share CPU cache), then performance will be impacted.

---

