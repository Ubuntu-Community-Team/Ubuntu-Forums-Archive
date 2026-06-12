---
title: "Modifying  special scripts globally"
date: 2023-03-13
forum: General Help
---

### Post by bjngchn on 2023-03-13
Someone (KG) was talking about, making some bad virus type of scripts uselless globally. Can such a thing be possible. I mean, maybe, when a program runs, it is dependent on a hardware which can be modified remotely, or depends on piece of code recalled from a central location.  I mean, this is like, there is a virus making everyone sick, and we send a signal from satellites, and make that virus harmless using a special frequency. Can such a thing be possible in computer world as well?   I mean, not everything of course, but some sophisticated stuff hidden from most people, can act like this if allowed.   For example, new cars can be controlled remotely, can there be a way to disable such features on all cars at once, without affecting other functions of  of cars?

---

### Post by TheFu on 2023-03-13
Seems like chat to me. I see no specific help request.
There are no viruses that work globally, because we all run slightly different OSes.
Almost anything bad that can be imagined can be created. It will need to extremely flexible to take advantage of the specific details of the system(s) involved. If the attack vector requires a specific setup then all the systems that don't have that setup won't be impacted.  MS-Windows viruses are an example.  They don't work on other OSes, unless there's an MS-Windows emulator and that emulator is sufficiently like the real thing to be susceptible.

Not all new cars can be controlled remotely, but some have flaws, usually withing a specific year and model, that can be abused.  It isn't an "all cars" thing, since some new cars don't have any OS and use disconnected computing. They all have slightly different OSes, if they even have any OS.  Real-time programming like used in control systems doesn't always have any OS.

Not all satellites can be hacked using the same methods either. They are all slightly different ... er ... so I hear.
Being hacked usually involved 3 steps.
[LIST=1]
[*]  determine the target OS/system
[*]  find a working exploit to gain access to the system
[*]  once on the system, determine how to elevate privileges, 
[*]  pull the specific version of code desired (small enough, correct architecture, correct OS, leverages existing tools already installed, etc.),
[*] hide that code somewhere that it won't trivially be found (in-memory objects are used for this, so are hidden directories or directories with very odd names, 
[*]  then run it.
[/LIST]

So ... possible comes down to "it depends on the details." There's no magical, works everywhere, exploit, that always works.

---

### Post by bjngchn on 2023-03-14
Thanks. There are many possibilities, but do they exist, is another question. For example inside a chip there can be unwired aetherical connection (like a wormhole) noone can check, and it can shortcircuit some data without anyone's knowledge.

---

### Post by TheFu on 2023-03-14
> **bjngchn said:**
> Thanks. There are many possibilities, but do they exist, is another question. For example inside a chip there can be unwired aetherical connection (like a wormhole) noone can check, and it can shortcircuit some data without anyone's knowledge.

No commercial chip maker would want that, so they'd strive to ensure it doesn't happen.  There are bugs, of course and sometimes a nation might request a "special" run of chips with a special flaw to be used for national security reasons. In some countries, the national govt can force companies to create whatever they demand. Fortunately, that isn't the situation with most developed countries. Companies there refuse to do what their govt ask and fight it in court if it is bad for the company's customers, regardless of national boundaries.

---

