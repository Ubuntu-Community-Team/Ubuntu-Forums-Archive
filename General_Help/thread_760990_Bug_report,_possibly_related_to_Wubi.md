---
title: "Bug report, possibly related to Wubi"
date: 2008-04-20
forum: General Help
---

### Post by QwUo173Hy on 2008-04-20
There was a problem with booting Ubuntu reported [at launchpad.net.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219349") At first I thought the bug was kernel related until I found out that both reporters were using Wubi to install.

Wubi doesn't seem to be listed as a package that I can assign the bug to so I decided to post here in case someone can help me assign it properly.

Regards,
Jarlath

---

### Post by ago on 2008-04-20
That is possible.

Could be that the swap file is fragmented? Can some kernel dev also look into this?

A quick workaround might be to rename c:\ubuntu\disks\swap.disk -> noswap.disk

---

