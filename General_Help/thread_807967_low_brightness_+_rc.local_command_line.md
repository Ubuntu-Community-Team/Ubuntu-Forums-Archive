---
title: "low brightness + rc.local command line"
date: 2008-05-26
forum: General Help
---

### Post by _godbout_ on 2008-05-26
Hi there,

I'm trying to fight against this low brightness at startup. Each time I've got the minimum brightness. Then I found this command line to make the brightness to 100%. I put it in the rc,local file, hoping that at each startup, the line will be executed and force the brightness to max. But it doesn't work. I used to read that the rc.local was executed by the root, so I shouldn't have any trouble with the privileges, right? Once I'm under gdm, if I open a terminal and type sudo /etc/rc.local, the script works and the brightness also, then.

Do you have any idea of why it doesn't work? Is the rc.local not run at startup? Is it run before the problem of the brightness occur? (10% of the progress bar under the splash). Any other idea?

Thanks in advance!

---

