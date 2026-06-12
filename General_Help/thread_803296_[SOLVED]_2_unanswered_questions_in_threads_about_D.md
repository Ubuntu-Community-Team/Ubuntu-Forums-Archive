---
title: "[SOLVED] 2 unanswered questions in threads about Desktop effects.."
date: 2008-05-22
forum: General Help
---

### Post by Donalb on 2008-05-22
Hi all, this isn't (yet) a question about not getting desktop effects running, but in many threads asking about effects, I've seen these 2 points raised but not answered. My apologies if I'm wasting anyones time but I've searched a lot of threads and haven't found the answers to these and I'd like some understanding so go with my learning Linux.

1:
Many people point out how desktop effects ran in Gutsy or Edgy etc, but not in Hardy. It usually segues to a disusion about their particular problem.

So I don't understand why this would be the case. 

What about the LiveCD? Why would Desktop effects work on the LiveCD but not on the installation,,,,OR....what about other Distros?

I had Desktop effects work on the LIVECD of 7.04, installed 7.10 (where they didn't work), don't work in 8.04 Hardy but DO work on the LiveCD of PCLinuxOS2007.

2:
In troubleshooting the problem for particular people, one of the first places people are pointed is the System>Administration>Hardware Drivers to see what graphics drivers are identified. But some people have said nothing shows here (as is the case with me). In many threads if it's NVIDIA it seems to show here but ATI often doesn't (again me here, older integrated ATI 9000). This I also don't understand, why would this be the case? (That something like an older ATI, which is using the default open source driver, isn't visible).

Thanks for the time on reading and any subsequent info!
Regards
Donal

---

### Post by Forlong on 2008-05-22
> **Donalb said:**
> 1:
Many people point out how desktop effects ran in Gutsy or Edgy etc, but not in Hardy. It usually segues to a disusion about their particular problem.

So I don't understand why this would be the case. 

What about the LiveCD? Why would Desktop effects work on the LiveCD but not on the installation,,,,OR....what about other Distros?

I had Desktop effects work on the LIVECD of 7.04, installed 7.10 (where they didn't work), don't work in 8.04 Hardy but DO work on the LiveCD of PCLinuxOS2007.
Ubuntu blacklists certain setups.
> **Donalb said:**
> 2:
In troubleshooting the problem for particular people, one of the first places people are pointed is the System>Administration>Hardware Drivers to see what graphics drivers are identified. But some people have said nothing shows here (as is the case with me). In many threads if it's NVIDIA it seems to show here but ATI often doesn't (again me here, older integrated ATI 9000). This I also don't understand, why would this be the case? (That something like an older ATI, which is using the default open source driver, isn't visible).
Sounds like you are running Ubuntu on a laptop with the ati/radeon driver. That is one of the setups I was referring to.
Run [Compiz-Check]("http://ubuntuforums.org/showthread.php?t=799070") to make sure. It will also help you fix it.

---

