---
title: "X-server freeze (NVRM and xid)"
date: 2007-07-05
forum: General Help
---

### Post by Morientes on 2007-07-05
Hi

Every once in a while it seems my x-server hangs completely. It happens very rarely but it has happened twice since I installed feisty (about the time it came out). The first time I did not look in the log but the second I did and I found this:

```

 24 Jul  3 22:20:47 morten-desktop kernel: [42866.662617] NVRM: Xid (0001:00): 16, Head 00000000 Count 003476ad
 25 Jul  3 22:20:55 morten-desktop kernel: [42874.650518] NVRM: Xid (0001:00): 16, Head 00000000 Count 003476ae
 26 Jul  3 22:21:03 morten-desktop kernel: [42882.638416] NVRM: Xid (0001:00): 16, Head 00000000 Count 003476af
 27 Jul  3 22:21:11 morten-desktop kernel: [42890.626315] NVRM: Xid (0001:00): 16, Head 00000000 Count 003476b0
 28 Jul  3 22:21:19 morten-desktop kernel: [42898.614217] NVRM: Xid (0001:00): 16, Head 00000000 Count 003476b1
 29 Jul  3 22:21:27 morten-desktop kernel: [42906.602115] NVRM: Xid (0001:00): 16, Head 00000000 Count 003476b2
 30 Jul  3 22:21:35 morten-desktop kernel: [42914.590015] NVRM: Xid (0001:00): 16, Head 00000000 Count 003476b3
 31 Jul  3 22:21:43 morten-desktop kernel: [42922.577914] NVRM: Xid (0001:00): 16, Head 00000000 Count 003476b4
 32 Jul  3 22:21:51 morten-desktop kernel: [42930.565814] NVRM: Xid (0001:00): 16, Head 00000000 Count 003476b5
 33 Jul  3 22:21:59 morten-desktop kernel: [42938.553713] NVRM: Xid (0001:00): 16, Head 00000000 Count 003476b6
 34 Jul  3 22:22:07 morten-desktop kernel: [42946.541611] NVRM: Xid (0001:00): 16, Head 00000000 Count 003476b7
 35 Jul  3 22:22:15 morten-desktop kernel: [42954.529513] NVRM: Xid (0001:00): 16, Head 00000000 Count 003476b8
 36 Jul  3 22:22:23 morten-desktop kernel: [42962.517412] NVRM: Xid (0001:00): 16, Head 00000000 Count 003476b9
 37 Jul  3 22:22:31 morten-desktop kernel: [42970.505311] NVRM: Xid (0001:00): 16, Head 00000000 Count 003476ba
 38 Jul  3 22:22:39 morten-desktop kernel: [42978.493210] NVRM: Xid (0001:00): 16, Head 00000000 Count 003476bb
 39 Jul  3 22:22:47 morten-desktop kernel: [42986.481111] NVRM: Xid (0001:00): 16, Head 00000000 Count 003476bc

```

Does anyone know what it is? It seemed that it happened just before the freeeze.

EDIT: I should add that my computer generally is very stable. And there are no problems in windows as far as I can tell. But of course I can't rule out that it's a hardware failure of some sort.

---

### Post by Morientes on 2007-07-11
bump

---

