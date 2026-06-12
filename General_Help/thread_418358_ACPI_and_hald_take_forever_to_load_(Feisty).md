---
title: "ACPI and hald take forever to load (Feisty)"
date: 2007-04-22
forum: General Help
---

### Post by bhtooefr on 2007-04-22
I'd love to post in the [thread](http://ubuntuforums.org/showthread.php?t=397138&highlight=hald) already started for this, but the forum it's in is locked. :mad: 

So...

When booting, the system drops to text (instead of the graphical boot) when it loads the ACPI modules, and sits there for a couple minutes doing nothing. (Ctrl-Alt-F1 through F8 work, however.) It does the same when starting hald. Any suggestions for diagnosing this?

---

### Post by chrisccoulson on 2007-04-22
My machine sits around doing nothing for a bit when loading hal, occasionally switching to text mode. It's nowhere near as bad as a couple of minutes though. It averages 8 - 9 seconds per boot and sometimes longer.

I was previously running Dapper on this machine, and it didn't exhibit this problem. Boot time was much quicker. I've got no idea what might be causing it.

I've attached my bootchart

---

### Post by bhtooefr on 2007-04-27
Here's a bootchart...

The problem appears, in my case, to be in modprobe, and in hald-addon-stor, if I'm interpreting this correctly.

---

### Post by chrisccoulson on 2007-04-27
Have you seen this thread too: [http://ubuntuforums.org/showthread.php?p=2544029]("http://ubuntuforums.org/showthread.php?p=2544029")

Sorry, I can't offer any suggestions at the moment, but maybe there's someone else who can.

---

