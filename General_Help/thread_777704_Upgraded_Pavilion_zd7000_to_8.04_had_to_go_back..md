---
title: "Upgraded Pavilion zd7000 to 8.04 had to go back."
date: 2008-05-01
forum: General Help
---

### Post by ckaga2000 on 2008-05-01
Okay After searching and searching I can't find anything that resembles what I encountered. Two days ago I noticed Update Manager was anouncing a new Distro was available, so I upgraded to it because so far upgrading has worked quite well for me.

Once I'm running at 8.04 (Hardy Heron I guess) I noticed something quite disconcerting. My CPU fan was cycling up like I was running a YouTube video or something silimilar, but I wasn't doing anything. My first instinct was to run "top" to se if updatedb or pre-link was running. Neither were nor could I see anything running at all.

So I ran gkrellm. It was reading 0%/1% for the most part and never exceeded 6% for either CPU. Yet the fan was running like crazy. I also tried the gnome system nonitor. It registered more activity, but top confirmed that this was the monitor itself. Still it was 6-15%. 

In 7.10 this sort of fan activity usually accompanied 50%/50% CPU activity or more.

To make a long story short, all my Google searches either yeilded comparisons to Windows, an off hand mention of something similar (Which only said that the person downgraded) and on bug report which was actually about RAM not CPU (And closed as "Not a Problem").

I'm now back to 7.10, and wondering if I should file this as a bug. Since I downgraded without really investigating in any detail the above is about all I can give for a description.

Does anyone have any sugesstions? Has anyone else seen a similar problem?

---

