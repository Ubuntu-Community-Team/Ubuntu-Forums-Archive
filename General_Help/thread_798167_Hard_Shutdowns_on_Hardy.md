---
title: "Hard Shutdowns on Hardy"
date: 2008-05-17
forum: General Help
---

### Post by Scruffynerf on 2008-05-17
Has anyone else noticed that when quitting to shut down Hardy, it shuts down fiercely?

I'm noticing on quitting that there are a few error messages (they go by too fast to notice) then the usplash appears, indicating a normal shutdown progression, then about half-way through, the machine just powers off, and the hard drives can be heard spinning down.

I recall that this was an issue with some people when Feisty was introduced, but I can't locate the threads?

Anyone have any ideas?

---

### Post by hardyn on 2008-05-17
there are some reports... file your bug report with SPECIFIC hardware / soft ware discriptions.  There are a few users that are having trouble with the kernel changes in hardy; unfortunately you seem to be one of them.

one thing you can do is after a reboot, open up the log files, and see actully what it is complaining about.

---

### Post by Scruffynerf on 2008-05-18
Thanks. Which logfile in particular should I be looking for? There's 53 items in /log.

Also, where do I file bug reports? Is it the Launchpad thing?

cheers

Edit: Kernal 2.6.24-16-generic BTW

Edit 2: I've also tried adding in *acpi=force noapic* into the grub menu, which doesn't help. 

I've read through the logs and text documents in /log that match the timestamps, however I cannot see any faults marked in them.

---

### Post by hardyn on 2008-05-18
yes, the lauchpad; read intructions on filing a proper bug report.
there is a log viewing tool, not in front of my machine to tell you exactly where.

there is a .17 kernel available from what i understand, and even the "itrepid" pre-alpha kernel.  try the .17 kernel and see if it helps any; but i would suggest to stay away from the pre-alpha kernel unless you would like a project... help will NOT yet be available for the intrepid ibex kernel.

---

### Post by Scruffynerf on 2008-05-19
Well, I filed a bug report, with what I hope is the right level of info.

[https://bugs.launchpad.net/ubuntu/+bug/231539](https://bugs.launchpad.net/ubuntu/+bug/231539)

Problem is, I'm wondering if this will get lost in the noise.

---

