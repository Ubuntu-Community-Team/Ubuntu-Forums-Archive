---
title: "Too much RAM is being used"
date: 2007-07-09
forum: General Help
---

### Post by ianthepetrock on 2007-07-09
Hey,
Heres my current setup. I installed regular Ubuntu on a computer and removed the GUI to make it a server. When i start the server, the "top" command reports 100mb of ram being used. I only have 512mb  so its kind of a lot for me. I have 82 total processes running which seems like alot... Are there more programs i should remove to make it more like a server installation? 

Another problem related to this is that RAM is constantly leaked whenever I'm on the website hosted by the server. I'm using apache2. If i load a big image, more ram is used and never goes back to being free...
:confused:

---

### Post by marsbt on 2007-07-09
Linux uses as much RAM as is available. So after some time almost all your RAM will be indicated as being used. However, when a new process requires more RAM, Linux leaves the RAM which is not being currently use (kind of on-hand cache). So don't worry if your system uses all the RAM. Its the *system load* you should be worried about.

For a GUI-less install, I think the Alternate disc is the one that you should use for installation. It will install only those packages which are required by your needed applications and the basic OS.

---

### Post by az on 2007-07-09
> **ianthepetrock said:**
> Hey,
Heres my current setup. I installed regular Ubuntu on a computer and removed the GUI to make it a server. When i start the server, the "top" command reports 100mb of ram being used. I only have 512mb  so its kind of a lot for me. I have 82 total processes running which seems like alot... Are there more programs i should remove to make it more like a server installation? 



I have a web server in in my basement running Ubuntu LAMP and Drupal:


Tasks:  49 total,   2 running,  47 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.3%us,  0.0%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    256116k total,   251384k used,     4732k free,    38216k buffers
Swap:   746980k total,       80k used,   746900k free,    75376k cached



Depending on what your web application is, I can't tell how many processes should be running.  Exactly what did you remove to get rid of the Desktop?

---

### Post by ajgreeny on 2007-07-09
You will get a much better idea of ram usage with the command **free -m** in a terminal.  Look for the line that shows something like this:-
                   total       used       free     shared    buffers     cached
Mem:          1011        763        247          0         22        548
*-/+ buffers/cache:       193        817*
Swap:         1953          0         1953

The line in italics is the important one and shows the amount of ram actually in use rather than the amount that has been in use at any time in the session.  Linux does not free up ram for the sake of it like windows, but keeps info in ram until it needs the ram again, thus making the system faster than searching the hard disk for the info again.

---

### Post by OoooMatron on 2007-07-09
unused ram is wasted ram. a kind of psychological mind **** left over from people using microsoft is the best way to describe it :D

---

### Post by ianthepetrock on 2007-07-09
Thanks everyone. Using the "free -m" command reveals that not as much ram is actually being used.

---

