---
title: "rsync a complete system over network"
date: 2008-05-26
forum: General Help
---

### Post by jahst on 2008-05-26
Hello,
Been searching for a long time but was never able to find a specific guide for what I'm trying to do. I hope it's not impossible.

I setup all my xubuntu installs with a "guest" account that gets rsynced from a root folder on the same computer at computer startup. This way, if guest (who has no privileges) messes up the desktop, menus, backgrounds, but usually settings for any programs in their account, they are automatically reset when the computer is restarted. Works like a charm.

However, I'm still new to linux and learning everyday. So I often find mistakes I have made, or settings I need to fix or programs I need to include / exclude. But I need to fix them on all my machines (around 30). Obviously this isn't fun fixing the same mistakes over and over. Likewise, it isn't fun going to each machine and logging in as root to download updates etc and it requires a lot of bandwidth.

So, I was wondering if there is a way to rsync a complete system over the network. So that when restarted, instead of rsyncing the "guest" settings from a local folder in the root directory, it would rsync the complete system from someplace on the network. 

Basically, I want a way to make changes on a single computer propagate to the others.

Any help Please.

---

### Post by unutbu on 2008-05-26
Maybe [clonezilla]("http://www.clonezilla.org/") fits the bill.

---

