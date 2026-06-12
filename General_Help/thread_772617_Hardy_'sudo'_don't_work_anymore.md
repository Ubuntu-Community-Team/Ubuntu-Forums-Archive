---
title: "Hardy 'sudo' don't work anymore"
date: 2008-04-28
forum: General Help
---

### Post by Popaul on 2008-04-28
Hi! I've upgraded to Hardy from Gutsy a few days ago, and am trying to get to terms with a few problems. First one, not too bad but strange:
in Terminal, 'sudo' brings me "sudo: unable to resolve host Compaq" (Compaq is name of PC).
However, 'gksudo' does the trick and the usual window pops up to ask the password etc...
Why is that? In Gutsy (and Fetsy etc..), simple 'sudo' worked fine.

A possibly related issue is that when trying to start Synaptic from the menu, I get nothing, just the little timer turning for a while and then nothing. I have to go into any menu that gives an 'unlock' button (like System/Administration/Users & Groups for example), which brings the password pop-up window, and then I can start Synaptic.

Any clues?

Thanks for any help!

---

### Post by A$h X on 2008-04-28
Boot into recovery mode and type:
> sudo nano etc/hosts

In there delete the domain name after your PC's name. For example change:

> 192.168.1.1 compaq.network

to


> 192.168.1.1 compaq

The line should be underneath a line reading "127.0.0.1 localhost" or something similar. Press ctrl+z to exit and Y to save. Once your back to the terminal, type "exit" and you boot into your desktop and everything will be fine. :)

---

### Post by Popaul on 2008-04-28
Thanks a lot, A$h X!

Both problems fixed.

---

