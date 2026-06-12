---
title: "Firefox 100% cpu and acpi/powernowd scaling stops"
date: 2008-07-09
forum: General Help
---

### Post by Execute_Method on 2008-07-09
I am having and issue with firefox 3.0. Some web pages are causing 100% cpu usage and freeze firefox. I know firefox can be a resource hog, but something else tells me there may be something else going on.

When this problem exhibits itself, my cpu stops scaling and sits at full scale(even with 1-2% load). I am using powernowd and acpid. I do not have apmd installed ( I removed it today thinking it may be causing a conflict).

This happened with [www.yahoo.com](www.yahoo.com) today, and it also happens with pages containing flash (when I first noticed this). I have removed flash 9 and installed flash 10 beta (which has ubuntu support). The problem persists. I have not tried yet to remove/reinstall firefox, which will be my next troubleshooting step.

If anyone could give me some insight or have any suggestions on troubleshooting I would much appreciate the help.

There are no messages in any of the logs (system log viewer) pertaining to these events. So, if you have any other suggestions of where to look for the error please let me know.

Thank You in advance.

---

### Post by Execute_Method on 2008-07-09
OK, tried to remove/reinstall firefox, with a reboot after to get my cpu scaling going again and problem persists. [www.yahoo.com](www.yahoo.com) causes 100% cpu usage then my cpu scaling doesn't work any more.


:confused:

---

### Post by Execute_Method on 2008-07-10
wow, no insight? Should I post this somewhere else?

---

### Post by rialto on 2008-07-10
I've been having the same problem and it seems whenever there's a multimedia area for the page the whole computer just sits to load the entire page!  I was just going to post this problem, but you beat me!  I've tried many different websites and after like 4 minutes of waiting the computer finally stops to let me view the page and scroll down.  Someone PLEASE HELP US!

---

### Post by rialto on 2008-07-10
I found this link and it seems this problem is with many many other people and it's actually firefox 3.

[http://ubuntuforums.org/showthread.php?t=845229&highlight=firefox+lag](http://ubuntuforums.org/showthread.php?t=845229&highlight=firefox+lag)

There's detailed instructions on there to uninstall Firefox 3 and install Firefox 2 on there also.

I hope this helps.

update:  I was able to get Firefox 2 working ALOT smoother than Firefox 3 on my computer.  Good luck! Just follow the instructions and you should be fine =)

---

### Post by Execute_Method on 2008-07-10
Thanks Rialto, I actually just installed FF2 last night to troubleshoot this, I haven't had a chance to check it yet though (working and all). Hopefully this will solve it for me as well.

---

### Post by Execute_Method on 2008-07-10
BTW, Rialto
Did you happen alter your about:config at all in Firefox3?

---

### Post by Execute_Method on 2008-07-11
Nevermind, I thought it might have to do with some of the things I set manually in about:config. However this is not the case as a fresh profile did not change it. Problem persist after purge, manual profile removal then reinstall

---

### Post by nittybitty on 2008-08-05
Lovely that software part of the FSF movement is so horribly defective on Linux but works great on Windows. I am not sure the Firefox team gets it.

I know opera does. Great browser with none of these problems.

---

