---
title: "Use another machine's CPU/RAM"
date: 2008-04-24
forum: General Help
---

### Post by Perkins on 2008-04-24
I have an old Ubuntu server which collects statistics and draws graphs.  It's not a very big machine, it's got a 2Ghz processor and 1Gb of RAM.  For what I normally do with it, it works just fine.

Now some of the higher ups would like a graph drawn for the entire last year...  I have hacked over the graphing routines to break the data into small enough chunks to be processable, but, if my calculations are correct, at the rate it's going it will take about four days to churn through it all.


That's the explanation for why I'm about to ask what might seem like an insane question.  I'm sitting here next to my new multi-processor desktop with several gig of memory, and thinking, "gee, wouldn't it be nice if I could tell the server in the back room to just run the job on this thing."

I have found several articles and software packages for various kinds of distributed processing under Linux, so far they all talk about setting up a cluster from scratch.  That's not very useful for this kind of thing.  

I'm wondering if any of you out there who have more experience with this kind of thing have run across something that lets you temporarily make two machines share computing power, that can be installed into an already operational system.

Sorry if this is in the wrong category, but I didn't see a more specific one that fit.  Feel free to move it.

---

### Post by mrollings on 2009-09-11
I don't know of a way that you can just share resources like that. However you can easily share a folder on a harddrive via samba or NFS, and then just get your program to issue half (or more) of the processing to your computer.

I guess what's next depends on what your programming in, because if you've written the program in php, you could simply have a copy of the program on your computer and use curl from your server to execute the program, either sending the result back through curl or writing directly to a shared folder. In python you could use urllib or something similar to do the same.

---

### Post by Perkins on 2009-09-11
This was a database program and one of the queries I was being asked to run against it was beyond the capabilities of the hardware to complete.  Insufficient memory and too little processor power.

There are a number of ways to do this, but, as it turned out, all of them require serious modification of the system and are not the kind of thing one would wish to attempt to install on a production system.

The solution ended up being to rewrite the data processing routines to pull the information in chunks.  It took a considerable amount of time and effort, and introduced the possibility of slight errors, but it fell within the acceptable bounds, so I went with it.

---

