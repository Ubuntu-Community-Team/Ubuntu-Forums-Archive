---
title: "Where did all the updates go?"
date: 2006-07-08
forum: General Help
---

### Post by flabbah on 2006-07-08
I installed Dapper on a box yesterday and upon the first boot the update notifier said there were 105 updates. There were a lot of gnome things in there.

I installed Dapper on a box this morning and there were only 22 updates - no gnome things.

Anybody have any ideas?

---

### Post by PingunZ on 2006-07-08
Can it be a different sources.list
Maybe some of your repo's werent available at that time ...

Grtz PingunZ

---

### Post by flabbah on 2006-07-08
> **PingunZ said:**
> Can it be a different sources.list
Maybe some of your repo's werent available at that time ...

Grtz PingunZ

I think I know what happened. Maybe during the text-mode install, the installer went out to the network for some reason and did not see several mirrors available. When I went into the "Repository" setting of Synaptic, most of my Binary / official repos were turned off. I found this extremely unusual. In the 40 or so Ubuntu installs I have done, I have never seen this. The update tool is literally the first thing I click on when I boot into a new install for the first time.

---

