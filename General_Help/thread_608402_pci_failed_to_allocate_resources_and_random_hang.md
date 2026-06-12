---
title: "pci failed to allocate resources and random hang"
date: 2007-11-10
forum: General Help
---

### Post by ultimatsz on 2007-11-10
i refer to [http://ubuntuforums.org/showthread.php?t=601828]("http://ubuntuforums.org/showthread.php?t=601828")


during boot these came out

```
[   20.591877] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   20.591921] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   20.591962] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   20.592002] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   20.592043] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   20.592083] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[   20.592124] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[   20.592164] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[   20.592205] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
```

i thought that was not an issue... i have random hangs with ubuntu gutsy .. windows will turn black and white.. however.. compiz still works... i post a topic on nvidia problems and i kind of get a solution.. but it did not work.. so it should be because of the core2duo procesor i think...  or the PCI problem


anyhelp so that i will not get random hangs?

---

### Post by paulomarciano on 2008-03-29
I have the same problem. Aparently a BIOS update should solve it, though i'm unable to do one. From what i've read, it's the BIOS that fails to allocate the resources for the PCI controller. Anyone knows how to solve this using boot parameters or like?

---

