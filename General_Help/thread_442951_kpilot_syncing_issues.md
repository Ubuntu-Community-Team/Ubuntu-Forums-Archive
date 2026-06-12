---
title: "kpilot syncing issues"
date: 2007-05-14
forum: General Help
---

### Post by mrchaotica on 2007-05-14
I recently installed Kubuntu Feisty on my Thinkpad x60 tablet (and am really pleased with it, aside from the lack of tablet-friendly applications -- it supports the laptop hardware out-of-the-box *better* than Vista!), and have been working on getting Kontact to sync with my Palm Tungsten E. Here are the issues I've encountered:

First, almost all the tutorials begin with "start up kpilot and type in the device file for the handheld (e.g. /dev/pilot, or maybe /dev/ttyusb0)." I spent several hours in severe frustration before I found anything that said "oh by the way, load the "visor" kernel module if you don't have those device files." Either Feisty is supposed to load that module by default and my install is broken, or those tutorial writers need to stop starting at step #2!

Second, I have to press the hotsync button on my handheld *before* starting the kPilot program; if I do it in the other order (start kPilot then press hotsync), it never finds the handheld. Is there a way to fix this problem (or better yet, set it so that kPilot starts automatically when I plug in handheld and press hotsync)?

Third, syncing fails to transfer appointment locations. The appointment title, time, and even category (which doesn't even work on my Mac -- I'd have to pay $50 for MissingSync for that!) transfer fine, but the lack of locations is a crippling problem since the #1 reason I even *have* a PDA is so that I'll be able to get to my classes, and for that I need to know where they are!

**Edit:** after further inspection, it turns out the locations *are* transferred to the handheld, but as "memos" attached to the appointments, rather than in the built-in location field. It's beginning to look like a bug in kPilot or Kontact to me, but if it works right for everybody else...

Does anybody have suggestions on how to fix these issues (or rather the second and third, since the first was more of a gripe than a problem)?

---

### Post by freund on 2007-05-15
I have had issues with kpilot myself in the past. I don't use the location feature so I can't help you there,

But since you are student check out
[http://groundstate.ca/tabletsoft](http://groundstate.ca/tabletsoft)

I use
xournal (pdf anotate)
and
a small virtual keyboard for KDE, Kavier at:
Get it at : [http://sebastien.huss.free.fr/?q=klavier](http://sebastien.huss.free.fr/?q=klavier)

al

---

