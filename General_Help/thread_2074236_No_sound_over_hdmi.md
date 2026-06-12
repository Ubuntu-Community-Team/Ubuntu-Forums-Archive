---
title: "No sound over hdmi"
date: 2012-10-21
forum: General Help
---

### Post by jakslev on 2012-10-21
I have no sound. Anyone knows what to do? Issue is when connecting HDMI to the tv. It worked perfectly before on 12.04

---

### Post by leecasey on 2012-10-21
> **jakslev said:**
> I have no sound. Anyone knows what to do? Issue is when connecting HDMI to the tv. It worked perfectly before on 12.04

Probably best off creating a new post rather than hi-jacking mine ;) Seems there are some problems with drivers etc though. 

How quickly are these issues normally resolved?

---

### Post by nothingspecial on 2012-10-21
Question moved to it's own thread.

---

### Post by alain.g on 2012-10-21
Hello

Try this : 
open a terminal & run "alsamixer". 
With the right arrow, go to "S/PDIF" (or equivalent).
If it's on "MM" (mute), change to "OO" by pressing the "m" key.

---

### Post by jakslev on 2012-10-24
> **nothingspecial said:**
> Question moved to it's own thread.

uhm.. where to? :-o

---

### Post by bomski on 2012-10-25
I also had some issues with configuring sound output via optical instead of HDMI using 12.04 and XBMC; after much reading I found that installing the medibuntu package resolved these issues for me; might be worth a shot:

[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

---

