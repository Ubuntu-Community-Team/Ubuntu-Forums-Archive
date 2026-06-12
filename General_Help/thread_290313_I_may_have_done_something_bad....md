---
title: "I may have done something bad..."
date: 2006-11-01
forum: General Help
---

### Post by Jiraiya_sama on 2006-11-01
apparently, using apt-build to install build essential is not that great an idea, or so I've heard. While I've seen no negative effects just yet, I was wondering if anyone who has more knowhow on the subject can give me their opinion.

P.S.: There seems to be a benefit of doing this, the compiler seems to be able to use both my processor cores simultaneously now. Of course, this is pure speculation, but I've never seen anything gobble up 100% of cpu resources, unless I was running two intensive apps at once.

---

### Post by ciscosurfer on 2006-11-01
Unless in your System Monitor > Resources > CPU History, you see CPU1 and CPU2, you're not utilizing both cores.  To do that, you need either the linux-686-smp or generic kernels installed.

Apt-build is nice if you care about the speed of your apps.  For blazing app speed, you set your apt-build to strong, but it will take much longer to compile programs and you may have stability issues.

I would install build-essential normally and then when you want to compile source for other packages, you can then decide if you want to apt-build them.  Just my two cents.

---

