---
title: "Accessing a network printer on a dual-boot system"
date: 2007-08-17
forum: General Help
---

### Post by Solver on 2007-08-17
I have a rather unusual setup that I need assistance with for printer sharing. There are two networked computers, A and B. B is an Ubuntu machine. A dual-boots XP and Ubuntu and has a printer connected to it. I need B to use that printer. I have set up printer sharing from both operating systems on A and it works just fine. The problem is, I had to install two printers on B thus - one is a connection through Windows, another is a connection through Ubuntu.

It means that, in order to print from B, the correct printer must manually be selected, depending on which OS is presently running on A. It's not really satisfactory, though - what I would ideally want is just one printer showing up on B that automatically figures out which sharing protocol to use. Maybe it would be a script of some sort to detect whether A is currently running XP or Ubuntu (it can safely be assumed to be on and running either of these), and thus choose the appropriate printing method.

I haven't been able to find descriptions of similar issues so far, so help will be appreciated.

---

### Post by ACGarib on 2007-08-17
I have the exact same configuration that you have and I want to do the same thing you want to do. Too bad I don't know how. The only problem is I can't even get B to print on A (Vista or ubuntu). I followed this tutorial [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#head-6a3af6eb770f1dbc388e0574599943e463608bed](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#head-6a3af6eb770f1dbc388e0574599943e463608bed)
But I can't get anything to print. I guess you are one step ahead of me.

---

### Post by Solver on 2007-08-17
Similar instructions worked for me, I followed an official tutorial back when I was setting it up (with Dapper, I think). Nice to see someone else has this configuration, however.

---

### Post by Solver on 2007-09-14
At the risk of annoying everyone, a bump.

---

### Post by lionround on 2007-09-30
The tutorial worked like a charm.  Thanks a bunch.

---

