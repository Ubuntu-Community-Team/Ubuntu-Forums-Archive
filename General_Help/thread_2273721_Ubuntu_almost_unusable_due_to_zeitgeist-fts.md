---
title: "Ubuntu almost unusable due to zeitgeist-fts"
date: 2015-04-15
forum: General Help
---

### Post by flix3 on 2015-04-15
Hello.

I'm using Ubuntu 14.10 64 bit.
I had to switch from 4GB RAM to 2 GB RAM.

Now in the "System Monitor" the program "zeitgeist-fts" always consumes more than 1.0 GB (sometimes it can get up to 1.8 GB on so). 

Most of the time the HD keeps working (swapping memory I guess) and my Ubuntu system becomes unusable.

Browsing in the forum, I've seen plenty of users having the same problem back in 2012: that's why I believe that this problem will never be fixed.

In short: 4GB RAM -> OK, 2GB RAM -> change OS if you can.
That's my experience.

Any advice welcome :).
Thank you in advance.

---

### Post by user_of_gnomes on 2015-04-15
I removed zeitgeist-core and everything related to it. I run 14.04, though.

Also, this seems to be a [known and confirmed bug.]("https://bugs.launchpad.net/ubuntu/+source/zeitgeist/+bug/1256196")

I find that Ubuntu runs best with at least 4-gigabyte of RAM.

---

### Post by ian-weisser on 2015-04-15
> **flix3 said:**
> that's why I believe that this problem will never be fixed.

It will never be fixed *if you don't do something about it*.
Ubuntu improves when users who discover a problem get involved to fix it.

You are welcome to take charge of this problem: To review all the relevant bug reports, to consult with upstream on possible causes, to triage the bug reports (work them into a usable condition for an upstream developer to diagnose and fix), and to refer the triaged bugs to the upstream developers so they can fix it.

None of those steps requires technical knowledge. They are mostly communication skills - making polite, constructive contact with bug reporters and upstream and being the liason between the two. See the [Ubuntu Wiki Triage Guide]("https://wiki.ubuntu.com/Bugs/Triage") for how to get started.

---

### Post by flix3 on 2015-04-16
> Ubuntu improves when users who discover a problem get involved to fix it.You're right, sorry for my bad mood :oops:!
However as you can see it's a known issue and it's there since 2013... there's nothing that I can add to it.

P.S. I've found out that clicking on the "Ubuntu Dash" increases the memory usage of "zeitgeist-fts" a lot. Ubuntu it's still usable if I don't click on it... but I'll probably end up following                                                                             [**[COLOR=#000000]user_of_gnomes[/COLOR]**]("http://ubuntuforums.org/member.php?u=68265") advice.

---

