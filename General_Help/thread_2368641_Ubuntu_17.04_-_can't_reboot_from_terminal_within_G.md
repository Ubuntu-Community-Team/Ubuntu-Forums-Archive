---
title: "Ubuntu 17.04 - can't reboot from terminal within GUI"
date: 2017-08-13
forum: General Help
---

### Post by bikergeek2 on 2017-08-13
I have a brand-new HP ProBook 450 G3.  I wiped Windows off of it and installed plain-vanilla Ubuntu 17.04, which is now the only OS on it.  I have an unusual problem.  Typing "sudo shutdown -r now" inside a terminal window causes the system to hang:  no mouse cursor, nothing.  Can't flip over to a text console to see what's going on.  I tried turning off splash screens but the machine doesn't even get far enough into the reboot process as to show me the text screens where it's shutting down various things--it just freezes at the desktop.

I found something that suggested that the "cups-browsed" service had a habit of hanging on the way down, so I disabled it.  Didn't help.

Rebooting from the "cogwheel" menu works.  Flipping over to a text console with ctl-alt-F1, logging in, and typing "sudo shutdown -r now" works there.  So why doesn't it work from within a terminal window, inside the GUI?

Yeah, yeah, I know:  "Doc, it hurts when I go like that."  "Well, don't go like that."

But I've gotten used to doing much of my work within a terminal window after 25+ years of working on Linux and Un*x systems.  This whole thing has me very much scratching my head, and I'd like to fix it.

Thanks in advance for any help, it's very much appreciated.

---

### Post by ajgreeny on 2017-08-13
Try the command without **sudo** which has not been required for several Ubuntu versions now to shutdown or reboot.  You might also like to try command **reboot** in place of **shutdown -r now**

I am not sure why using **sudo** should make the command fail, but it is just me thinking out loud, so must be worth a try.

---

### Post by bikergeek2 on 2017-08-13
> **ajgreeny said:**
> Try the command without **sudo** which has not been required for several Ubuntu versions now to shutdown or reboot.  You might also like to try command **reboot** in place of **shutdown -r now**

I am not sure why using **sudo** should make the command fail, but it is just me thinking out loud, so must be worth a try.

Hi, thanks for the quick follow-up.  "shutdown -r now" without "sudo" doesn't work any better--the machine still hangs pretty much immediately. "reboot", however, works.  No clue what's going on.

---

### Post by ajgreeny on 2017-08-13
> **bikergeek2 said:**
> Hi, thanks for the quick follow-up.  "shutdown -r now" without "sudo" doesn't work any better--the machine still hangs pretty much immediately. "reboot", however, works.  No clue what's going on.
Well that's half-way to success, but I am not sure what you can do to make **shutdown** work properly.
What happens if you simply use the command **shutdown** with no extra options or arguments?

---

### Post by bikergeek2 on 2017-08-13
> **ajgreeny said:**
> What happens if you simply use the command **shutdown** with no extra options or arguments?

That works--the system schedules a shutdown for 1 minute in the future, and then it shuts down as scheduled and powers off.  "shutdown -h now" also works.  Plain "shutdown -r" also works.  "shutdown -r now", for some unaccountable reason, has now also started working.  I'm baffled.

---

### Post by ajgreeny on 2017-08-14
So am I!!

That's technology for you.

---

### Post by bikergeek2 on 2017-08-15
Regardless, thank you for the help, **ajgreeny**.  I guess we can mark this "Closed" at this point.

---

### Post by ajgreeny on 2017-08-15
Great news! By all means, please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

We do not mark threads as closed normally until they have been unused for a year and the system closes it automatically.

---

