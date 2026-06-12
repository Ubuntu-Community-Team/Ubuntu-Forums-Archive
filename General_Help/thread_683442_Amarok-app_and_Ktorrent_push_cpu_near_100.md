---
title: "Amarok-app and Ktorrent push cpu near 100"
date: 2008-01-31
forum: General Help
---

### Post by 3dmidi on 2008-01-31
I'm running a fully updated Gutsy AMD64 Kubuntu distro on a C2D laptop. It's a tri-boot system (though I rarely use vista or xp) where / is mounted on sda6, a reiser-fs partition. 

When I launch ktorrent it pushes processor usage near 100%. When I launch amarok, amarok-app does the same, and needs to be killed to exit. Both of these problems have begun occurring within the last two weeks.

Thanks in advance for any suggestions.
Drew

---

### Post by 3dmidi on 2008-03-13
So, my final solution was to nuke my amarok settings folder:

```
rm -r ~/.kde/share/apps/amarok
```

Crude, but effective.

---

