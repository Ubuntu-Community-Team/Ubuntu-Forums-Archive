---
title: "Upgrading Gnome 2.14.3 in Dapper Drake to 2.16 RC 1 that's in knot2"
date: 2006-09-03
forum: General Help
---

### Post by javaman67 on 2006-09-03
Hi everyone,

Has anyone tried updating Gnome in Dapper Drake to Gnome 2.16 RC1 that's in Edgy/knot2 that just came out?  If so, how did you do it?......by changing sources.list to edgy, then updating?

Thanks...

Brian

---

### Post by mejy on 2006-09-03
> **javaman67 said:**
> Hi everyone,

Has anyone tried updating Gnome in Dapper Drake to Gnome 2.16 RC1 that's in Edgy/knot2 that just came out?  If so, how did you do it?......by changing sources.list to edgy, then updating?

Thanks...

Brian

If you try to update the gnome in dapper to that in Edgy, it will pull in so many dependencies that you'll just end up with a version of Edgy with sum risidual Dapper libraries that'll only make things less stable.  Furthermore, Edgy is in rough, pre-Alpha state and should NOT be used as your primary operating system since it'll break regularly.  Furtermore, many of the libraries will be from after the knot2 release so won't even be vetted not to be completely broken.

If you want tortry out Gnome 2.15 (It's still beta, odd gnome releases are betas), then download the knot2 ISO and install it either in a virtual machine (like VMWare Server) or on a sperate partition.

---

### Post by Anduu on 2006-09-03
Yup listen to **mejy**...what you want to do would not be a good idea...

---

