---
title: "[SOLVED] Sparc repository updates"
date: 2008-05-10
forum: General Help
---

### Post by pacarey on 2008-05-10
Hi guys,

Just wonder if you could clarify something for me. I've noticed that the other builds of ubuntu have been getting updates recently. Yet when I have tried connecting to gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/ there is no binary-sparc folder. Yet that folder exists in the other ubuntu builds feisty/gutsy

Have they moved the sparc updates somewhere else? Or is it just that are are none.

Paul

---

### Post by Rocket2DMn on 2008-05-11
It is possible that your mirror simply hasn't synced that directory with the main server yet.  Have you tried switching repositories from System->Administration->Software Sources ?

---

### Post by pacarey on 2008-05-11
I have found the solution to this problem. it appears that sparc updates are being handled by the repository at ports.ubuntu.com. After updating sources.list, the updates  are now starting to filter through.

Should have read the release notes earlier as the changes were mentioned in it.


Paul

---

