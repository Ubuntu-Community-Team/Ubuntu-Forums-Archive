---
title: "Average Joe Home Cluster"
date: 2006-10-12
forum: General Help
---

### Post by morequarky on 2006-10-12
I am frustrated.  I really really really want to have my own small cluster wired up working for me at home.  I am frustrated because it would be in my mind absolutely useless.  It is like upgrading your 32bit processor to 64bit hoping your web surfing becomes faster.

I would like someone to please convince me that doing such a ludicrous thing would be a good idea.

:)

---

### Post by h2gofast on 2006-10-12
> **morequarky said:**
> I am frustrated.  I really really really want to have my own small cluster wired up working for me at home.  I am frustrated because it would be in my mind absolutely useless.  It is like upgrading your 32bit processor to 64bit hoping your web surfing becomes faster.

I would like someone to please convince me that doing such a ludicrous thing would be a good idea.

:)

If I remember correctly their were two ways to do this and I don't remember which was which.  But, one type of cluster required that the applications be written specifically for a cluster.  i.e. you can't just run firefox written for x86 and run it off a cluster.  The second way could run regular apps but each cpu in the cluster would only run one thread at a time, so the benefits do not outweigh the overhead of dishing out each thread to a cpu.  I'm not a programmer so I could be wrong but I think I got the gist of it right.  

In other words it's not a good idea unless you want to rewrite a bunch of applications.  The source is available...

---

### Post by morequarky on 2006-10-13
32bit apps run on 64bit processors and the CoreDuo is really two processors correct? So aren't their bios or processor commands that will control or could control which processor does what?  I guess someday processors and bios could talk to each other and just know what to do when the OS makes the correct calls.

---

### Post by morequarky on 2006-10-14
I highly doubt it but just for clearification, Would a cluster make image or video editing faster?

---

### Post by morequarky on 2006-10-14
Could I install Ubuntu on top of a Linux server install with load balancing?  Would that send "something" to the other computers in the cluster?

Thanks

---

### Post by Ocxic on 2006-10-15
with you own cluster it would cut down compiling time when your installing from source, and lower proccesing time during large upgrades.

yes having a cluster would make video editing faster, as it uses a very large amount of cpu power for effects and transitions.

---

### Post by morequarky on 2006-10-15
What software/drivers would I install to make a cluster work pretty much out of the box?  Load-balancing server install?  Is there some VM ware that just works?  I can't find a free copy of Scyld, but I don't even know if that is what I need?  Is there a Debian(Ubuntu) Beowulf distro?

Sorry for so many questions.

Thanks

---

### Post by Ocxic on 2006-10-15
there is a variety of programs in synaptic for clustering you can install.

---

