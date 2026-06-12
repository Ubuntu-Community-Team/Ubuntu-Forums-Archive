---
title: "Unable to Boot into Ubuntu or Recovery Mode - BusyBox Wants to &quot;fsck&quot; OwO"
date: 2019-10-01
forum: General Help
---

### Post by mlisdreaming on 2019-10-01
My Ubuntu machine (newest version of ubuntu) will no longer boot, even into recovery mode. With or without recovery mode it'll boot into something called "BusyBox" telling me that it failed to "fsck" (sounds like a personal problem) and that I need to perform a "manual fsck." When using the command "fsck" it does nothing. No response and PC will still boot the same. "help" only lists available commands and it's not helpful at all.

---

### Post by CatKiller on 2019-10-01
fsck is a filesystem check.

The easiest way to do it is to boot into your install media's live environment and do it from there.

---

### Post by mlisdreaming on 2019-10-01
> **CatKiller said:**
> ...install media's live environment...
 I assume you mean the small packaged version used to install ubuntu from USB.

---

### Post by CatKiller on 2019-10-01
> **mlisdreaming said:**
> I assume you mean the small packaged version used to install ubuntu from USB.

Yes. When I first started using Ubuntu, it was a live CD. Then live DVD. Now live USB drives are most common.

It's a fully-functional Linux environment. It will have the fsck that you need, but it's got all the tools that you're familiar with including a web browser.

BusyBox has as many tools as it's possible to fit in without having an actual OS running, and it's very useful if you already know how to do what you need to do, but there's simply no room for user-friendliness.

---

