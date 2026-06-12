---
title: "Last Known Kernel to Allow iptables?"
date: 2006-10-10
forum: General Help
---

### Post by moore.bryan on 2006-10-10
[I]hoping for some help from the community on this one... on my previous install, i was able to get kernel 2.6.18 working with iptables AND firestarter with no problems.  i was an idiot and tried to upgrade to edgy... fried the install.  reinstalled and was, again, an idiot and tried initng... fried the install.  i'm sticking with dapper now, but i have a new issue... when compiling the 2.6.18 kernel, NO MATTER WHAT I DO, firestarter won't run properly and all i get are iptables errors.  iptables IS running, "sudo iptables --list" gives me a nice output of allowing everything, but i can't create any rules.  does any one out there know the last kernel to include iptables without any of these ridiculous, deep-rooted, seemingly hidden iptables references for xconfig?
also, on a side-note, does anyone have any idea why in the world iptables would be disabled by the new kernel?  is there something better out there i don't know about?  ;-)
[/I]

---

### Post by moore.bryan on 2006-10-12
*nobody?  wow... i can't imagine this isn't an issue.  the latest i found which has iptables already working and an unbroken firestarter is 2.6.15.27... the one in the repos.  does ANYONE have any info about other kernels?*

---

### Post by PriceChild on 2006-10-12
I've heard of this issue before during the Dapper Dev cycle... i'll see if i can find a thread for you.

Is there any specific reason why you are compiling your own kernel?

UPDATE

from [http://ubuntuforums.org/showthread.php?p=1544683](http://ubuntuforums.org/showthread.php?p=1544683)

[http://ubuntuforums.org/showpost.php?p=1547101&postcount=274](http://ubuntuforums.org/showpost.php?p=1547101&postcount=274)

I hope this helps.... (you've posted below it so unsure as to whether you've tried it.)

---

### Post by moore.bryan on 2006-10-12
[I]thanks, price... i've always compiled my own kernel... in fact, until i accidentally stumbled on a thread about it, i didn't even know there were kernels in ubuntu's repos!  sometimes i feel like such a fool.  the other main reason why i compiled my own was to get rid of some of the bloat.

any ideas about my other edgy/initng issues?  i was looking forward to edgy, but it just wouldn't load anything and then initng was a huge headache...
[/I]

---

### Post by PriceChild on 2006-10-12
> **moore.bryan said:**
> [I]thanks, price... i've always compiled my own kernel... in fact, until i accidentally stumbled on a thread about it, i didn't even know there were kernels in ubuntu's repos!  sometimes i feel like such a fool.  the other main reason why i compiled my own was to get rid of some of the bloat.I'm willing to bet that this is half placebo... Yes it will be slightly faster... but not too much to notice in most cases.
> any ideas about my other edgy/initng issues?  i was looking forward to edgy, but it just wouldn't load anything and then initng was a huge headache...
[/I]Don't know what other issues these are... but i'm guessing you haven't realised edgy's ditching the init start... moving to upstart.

Ensure you have ubuntu-desktop isntalled before ANY kind of upgrade to Edgy.

---

