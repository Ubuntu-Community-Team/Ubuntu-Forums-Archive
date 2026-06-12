---
title: "dvd::rip multi-core question"
date: 2007-09-27
forum: General Help
---

### Post by ashughes on 2007-09-27
I have a quad-core Q6600 and was wondering if there was any way to configure dvd::rip to utilize all four course at once.  Right now, it is using 25% CPU, which tells me it is using 100% of 1 core.  

Since I am using 2-pass encoding, it takes about 8 hours to take 1 dvd to xvid and I would like to cut this down if at all possible.

Thanks a lot.

---

### Post by un_dave on 2007-09-27
Haven't tested this out yet, but i have the same cpu, and would also be curious if you can get encoding software like this to use multiple cores. 

I would guess it has to do with how the software is written to utilise multithreading?

---

### Post by SeanTater on 2007-09-27
I had the same thing on a dual core. Here is how to fix it: make a cluster (using Cluster -> Control) with all four nodes on your computer. Then, when you would press "transcode", instead press "add to cluster", then "start" in the cluster control dialog. You may have to turn off "Use PSU Core" in the transcode, and also choose the number of frames per work unit. 20000 to 25000 usually is a good choice, as too many may not allow all the processors to work in parallel, while too few degrades quality.

---

### Post by -emory- on 2008-02-24
sorry to bump an old post, but this is a big problem for me too, is there any way you could (or anyone) explain what exactly you mean in that post? How do I add nodes for my other core? I just realized today that my friend's macbook (same specs, dual core, 1gig ram, 2.0ghz) rips and encodes a dvd to avi in about half an hour, compared to my hour and a half.... Thanks

---

### Post by wayfarer_boy on 2008-03-01
[LIST]
[*]Bring up the Cluster Control window in dvd::rip (Ctrl-M or select it from the Cluster menu)
[*]Add a new node, and enter the following:
[LIST]
[*]Name: cpu1
[*]Hostname: localhost
[*]Local data directory: /home/user/dvdrip-data (or wherever your dvdrip-data directory is located)
[*]Speed index: 100
[*]Node has dvd::drip data harddrive? Yes
[*]Node runs Cluster Control Daemon? Yes
[/LIST]Click Test settings, and if all runs OK, click OK to save the node.
[*]Repeat for each of your cpus, naming them cpu2, cpu3, and cpu4.
[*]When it comes to transcoding your DVD, rather than clicking Transcode, click Add to Cluster.
[*]A new window will pop-up - enter 25000 into the Number of frames per chunk field, then click OK.
[*]The project now appears in the cluster window's Project Queue.  Click on it, and click Start Project.
[*]Hopefully, all 4 of your CPUs will now be used to transcode the DVD!
[/LIST]

---

### Post by jonthysell on 2008-04-24
Another bump, I think I've found a better solution from the transcode man:

```
-u m[,n]
              use m framebuffer[,n threads] for AV processing [10,1].
```

When you go to add/edit a node in the cluster, the "Additional transcode options" recommends the use of -u 4,2 for dual core machines.

So if you still want to use clusters, then instead of four nodes, (one per cpu) you can just create one node for your computer and add the -u option.

Under "Additional transcode options" put -u m,n where n is 4 for quad-cores, and m is the number of buffers (I'm not sure what is optimal for m on a quad-core).

Otherwise, if you're not using a cluster with nodes, and just want to use the regular mode, just set the -u parameter "transcode options" on the "Transcode" tab before you start transcoding.

I just found this now, and it's sped up my transcoding (using -u 4,2 on a  dual core system) by about 100%.

---

### Post by jonthysell on 2008-04-27
Now that I've gotten into a swing of things (populating a media server), I've found that for transcode's -u m,n flag:

m = framebuffer ~ set higher to buffer more frames in ram while encoding
n = number of threads ~ set to the number of processors/cores that you have

If you have lots of RAM but maybe your drives aren't too fast, increase the frame buffer to speed things up.

On my 1.6GHz dual core with 3GB of RAM, I use -u 1000,2 (which uses both cores and ~ 800MB RAM).

Also, I've found that increasing the "process nice level" to 0, and closing anything extraneous adds another 5-10 fps.

Be happy.

---

### Post by vdawg on 2008-05-16
What exactly is the process nice level?

---

### Post by bsharp on 2008-05-16
It is the priority of the process. It is a number from -20-20 with -20 being highest priority and 20 being low priority.

---

### Post by jonthysell on 2008-05-16
Most processes (firefox, etc.) default to 0, so if you set dvd::rip to 0, you may experience slowdown with your other running programs.

But if you're leaving the rip on over a long period when you're not using the computer (say chaining several in a batch script),  the low priority of 19 will mean that the other system proceses that are still running (GNOME, firewall, various services) will get priority and rob you of 5-10fps.

Also, there's a limit at which increasing the m in -u m,n doesn't help anymore, now I set mine to -u 512,2 (though in actuality I could probably go lower).

---

### Post by tuomask on 2008-05-18
Thanks for the good hint jonthysell.
I have Q6700 quad core and setting the transcode option to -u 512,4 indeed creates 4 threads. But the CPUs are not 100% occupied. In fact I noticed that editing framebuffer size and number of threads does not have a significant impact on the overall encoding time. Setting nice to 0 on the other hand does make a difference.

---

### Post by tuomask on 2008-05-24
Running transcode with multiple threads does not seem to be very efficient, so it is better to create a local cluster in dvd::rip. In other words, if you have 4 processors create 4 nodes ( labelled cpu0,cpu1,.. for instance) in the dvd::rip cluster control window.

All of the nodes have the same parameters:
Hostname: localhost
Local data directory: root of your dvd::rip tree (under which the project directories are)
Speed Index: 100
Node has dvd::rip data harddrive: Yes
Node runs Cluster Control Daemon: Yes

The chunksize should be something big, 40 000 frames or so, so that the whole project is divided into 4 to 6 chunks. Since all the chucks will be transcoded in independent processes (which are merged in the end) all your CPUs will be 100% occupied (nice 0) saving a lot of time. You can check the CPU loads with htop.

For example, transcoding a full-length DVD took me only 47mins using local cluster with 4 nodes, while the same job took 96mins with the -u 256:4 option (no cluster).

I don't know if the speedup will be similar with dual core... probably not.

---

### Post by jonthysell on 2008-05-24
You're right, when I use -u 512,2 I don't get 100% processor usage (70-90% for each), but it did halve my encoding times.

I should have kept better records, but I did try encoding the same movie a half dozen different ways, though I didn't try the cluster method.

Is that 47 minutes for two passes, or 47 minutes per pass?

For me a 2 hour movie on my dual core with -u 512,2 and nice 0 took about 2 hours for a two-pass encode to xvid.

---

### Post by tuomask on 2008-05-25
47 minutes is the total time of two-pass encoding to xvid.
It makes sense, quad core should be rouhgly twice as fast compared to dual core.

If your CPU usage is 70-90%, I suppose you could still save a bit of time with the cluster method, but the difference would not be as big as with quad core.

---

