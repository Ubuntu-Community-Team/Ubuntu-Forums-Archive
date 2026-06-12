---
title: "JFS vs XFS"
date: 2006-12-05
forum: General Help
---

### Post by luca_linux on 2006-12-05
I'm thinking about trying some other file system (currently gone back to ext3 after a short experience with reiserfs) such as JFS and XFS that seem to be very good.
What's the best in your opinion?

I've read some benchmarks and as a result JFS seems to be very fast and light, with the lowest CPU consumption, and in the meanwhile very good at handling big files.
XFS, instead, seems to be a little faster than JFS, but with more CPU consumption and, according to someone, also a bit better than JFS at handling big files. Yet, I've heard of some stabilty issues, also caused by the current 4K kernel stack; I don't know if that is true or not.

That said, I was thinking about using JFS on my laptop and XFS on my desktop/server.

What do you think about?
Which one is better supported by Linux?

P.S.: I know IBM released JFS2 in 2001, but haven't figured out if it has been ported to Linux or not. It would be great if someone knew something else about that.

---

### Post by kerry_s on 2006-12-05
I use JFS for all my partions except boot, my boot is reseirfs. I use to run a mix of everything, but recently we had a few power outages & only my JFS systems were working perfectly. So when edgy came out i updated & changed all my partions to JFS. The only downside i found was with playing with other distro's that do not have JFS support. Now that i've used it for awhile, the only thing i would change is using a EXT2 partion as backup. Well thats my story, hope you have good luck with your choice.

---

### Post by luca_linux on 2006-12-06
Any other opinion/experience?

---

