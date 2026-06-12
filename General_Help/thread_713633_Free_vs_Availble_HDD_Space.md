---
title: "Free vs Availble HDD Space"
date: 2008-03-02
forum: General Help
---

### Post by andrewshalin on 2008-03-02
I've just installed Ubuntu 7.10 on my new HDD.

I did a full format and clean install. Ubuntu with all the programs I use takes up about 4GBs of space. All of my docs take up another 14GBs roughly.

When I check for available space and free space they don't match.

Here's a screenshot of what I mean. Where does the other 10-11 GBs go?

Thanks for any help.

-Andrew.

---

### Post by imtheguru on 2008-03-02
The missing space is = 10% of total space and is accounted for by reserved blocks.

Reserved blocks default to 10% of total disk space. See the man pages of tune2fs.

Cheers.

---

### Post by andrewshalin on 2008-03-03
Thanks a lot!

this helped:

> tune2fs -m 0 /dev/sda1

---

### Post by loganm10 on 2008-03-03
I use reiserfs (you can to choose it under "manual" when you are partitioning) I read its faster and free and avaliable space is the same (ie it doesnt waste 10%). I read its faster too but I dont think us humans can see the difference

---

