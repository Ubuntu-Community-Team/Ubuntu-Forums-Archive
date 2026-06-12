---
title: "With Vista's Explorer burned Data-DVD isn't readable under Ubuntu"
date: 2007-02-25
forum: General Help
---

### Post by darge0flex on 2007-02-25
One week ago I said to myself: give the microsofties a chance and test there newest os. I have to say: like every win version it sucks.

But that's not the problem. I've burned a dvd with windows explorer. An easy thing, just drag and drop the data files, wait a few minutes and everything went fine.

But now, back at edgy, the dvd isn't readable. Btw the dvd has no write/read-errors. When I insert the dvd I get this message in my logs:

```

[17200869.488000] hdc: irq timeout: status=0xd0 { Busy }
[17200869.488000] ide: failed opcode was: unknown
[17200869.536000] hdc: ATAPI reset complete
[17200875.308000] Unable to identify CD-ROM format.

```

I also tried it manually with every (!) available fs-type. From adfs to xiafs. :) Nothing works.

Maybe there is someone out there who know what new kind of evil filesystem MS has developed there? Or have I just to choose a newer kernel version? My system has the latest edgy one: 2.6.17-11-generic.

Thanks!

---

