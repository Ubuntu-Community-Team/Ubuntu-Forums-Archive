---
title: "Ubuntu and XP"
date: 2024-02-19
forum: General Help
---

### Post by jschmidling on 2024-02-19
I once ran Ubuntu virtually in XP but can't seem to figure out how to do it now.. years later.

The only tool that seems to be available is VirtualBox but this does not seem to support XP.

I don't want to ditch XP so Ubuntu must run virtually.

Any help?

Jack

---

### Post by guiverc on 2024-02-19
Windows XP is ancient, and the software on it is also a decade behind (EOL in 2014).

I still have a windows XP install here, it has two games that I may boot & run a few times a year (*those games will run on Ubuntu too, but the games seem to crash a bit, which on windows just throws you back to windows XP; same in Ubuntu except the screen resolution is left low res. that's a pain; why I kept XP*).

Windows XP has a HOST OS can be problematic due to the XP host software being so *outdated;* it won't be capable of running modern VMs (*windows 7 has the same problem; only as not as outdated as either  Vista or XP*).

Yes you can run Linux VMs on a windows XP host; however I suspect you'll be limited only to really old software (*older than the virtualization software you're using*). Virtualbox would run on windows XP, but the versions that will are ancient & limiting.

I have no issues with XP on a dual boot environment (2x Ubuntu installs + XP), thus its what I'd suggest  (*and I'll also suggest keeping your XP offline... I do mine*).

---

### Post by MAFoElffen on 2024-02-19
If you use your Google skills, search for "Download VMware Player 4.0.4 for Windows"

But, being Windows XP went End Of Life over 10 years ago, in 2014... Should you think about doing the opposite? (Running Windows XP in a VM from Ubuntu.)

---

### Post by TheFu on 2024-02-19
> **jschmidling said:**
>  Any help?

Wipe the system and load Ubuntu (an appropriate version for your hardware), then setup a VM to run WinXP under it.
You should backup anything you don't want to lose BEFORE doing this.

It is unreasonable to expect unsupported software to be supported indefinitely. Sorry.

---

