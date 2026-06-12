---
title: "Reduce Updates to a managable amount"
date: 2006-07-30
forum: General Help
---

### Post by SittingDuck on 2006-07-30
G'Day,

I have installed 6.06 from a DVD.  However on starting and connecting to the internet the Update Manager tells me there are 130 updates available with a total size of 184Mb.

Now I am limited to dial up and currently due to rain the lines will only let me connect at about 24kb/s, so I don't want to have to try and download 184 Mb.

With 130 Updates waiting, is there any sane way of limiting the Updates to small batches, preferably more important ones first.  All I seem to be able to do is check or uncheck each one individually which will take hours, and I bet I will uncheck one that is needed for another.

Thanks in advance for any help
SittingDuck

---

### Post by cstudent on 2006-07-30
130 is the number of updates since Dapper was officially released. You'll get  that large number any time you install Dapper. After that, things will quiet down. You can go into the synaptic settings and have it download in the background. It will quietly download when you are online and pick up where it needs to later until it has everything. In the mean time you can still use the system.

---

### Post by SittingDuck on 2006-07-30
Unfortunately at 24kb/s my calculations show about 61 hours of downloading, and when I try to download and do anything else using the internet the update downloads fail, as it's easy to saturate the link, and move onto the next file (which probably fails too).

I need a way to select a managable set of updates (probably 10 - 20 Mb) that I can leave over night, and then select the next lot.

---

### Post by cstudent on 2006-07-30
I think you can go into synaptic and under settings select filters. There should be a filter for upgradable (upstream). If so, close that menu and click on the custom button at the lower left corner. This should then show you only the packages that are wanting to be updated. Select the batch you want and then repeat the process when you are ready to download some more.

---

### Post by adamkane on 2006-07-30
Dialup Ubuntu users are faced with a stark choice.

Be satisfied with their CD installation or be willing to spend countless hours downloading updates.

Fortunately Ubuntu comes out with frequent CD updates, but you will have to order them for a few dollars via post (if you want to receive them sooner rather than later.)

You can try to install only the packages that you want/need at installation time, but you will end up with more errors than you can handle, and isn't a viable option for most.

---

