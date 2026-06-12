---
title: "need help...broke my dpkg (Solved)"
date: 2005-10-30
forum: General Help
---

### Post by GoldBuggie on 2005-10-30
I need help repairing dpkg. I found why apt-build doesn't work on other systems then i386 and I was trying to found a solution to that problem. In doing so I played around with dpkg(yes I know dangerous stuff). I did numerous things but one beeing installing a own compiled version. Now when I have tried to get back to what I had from the beginning I get some problems.

When I run synaptic and install whatever I get serious warning about "not finding files for <a lot of packages>, assuming not installed".

I think the problem lies in that the file that contains these package info aren't used or something. Since when I install let's say krename everything works. But when looking at the packages in synaptic it says not installed. But I can run it.

What to do??? I tried reinstalling dpkg but it says that it has a conflict with another package, which I have removed but since the file containing this info isn't updated..well..you see the problem I hope.

I neeeeed help. Something else then reinstall kubuntu please.

---

### Post by beefsprocket on 2005-10-30
Have you tried using dpkg with the --force option?

---

### Post by GoldBuggie on 2005-10-30
=D>:D whohooo..it worked.

Do not know why I missed that one. Only found --force-yes and that wasn't the thing I needed. But a small but yet major help from you gave me all the help I needed.
[LIST=1]
[*]man dpkg | grep force   
[*]dpkg --force-help   
[*]Download .deb package from repository   
[*]sudo dpkg --force-all -i dpkg_1.13.10ubuntu4_i386.deb [/LIST] 
Fixed everything for me:D. Ahhhh...now I can go back to loving (K)ubuntu once again. Thank you so much!!!

---

### Post by beefsprocket on 2005-10-30
[quote=GoldBuggie]Do not know why I missed that one.[/quote]

Something that is easily missed -- not at all obvious I should think. 

I can't say that I'm at all familiar with dpkg, preferring as I do, apt-get and synaptic when available. However, for those cases of breakage that can't be resolved so easily, cases that, ironically, I've learned to avoid based mostly on my aversion to dpkg, it is the place of origin to which one must return in times of crisis.

---

