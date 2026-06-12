---
title: "What happened to /sys/module/processor/parameters"
date: 2008-04-25
forum: General Help
---

### Post by peterff on 2008-04-25
Hi,

It seems that in Hardy the processor module can no longer be passed parameters through this directory, as was possible in Gutsy: The parameters directory no longer exists. I used the max_cstate file located in that directory to change the cstate of my processor, which stopped it from making a high-pitched whine. Does anyone know of an alternative way to change the cstate on the fly? I think one can pass parameters to modules using modprobe, but I don't want to have to reload the module every time I change the cstate.

---

### Post by peterff on 2008-04-26
Well, in case anyone else had the same question, I found the following in the changelog for kernel 2.6.24:

>     Date:   Sun Aug 12 01:39:27 2007 -0400
    
        cpuidle: Remove support for runtime changing of max_cstate
    
        Remove support for runtime changeability of max_cstate. Drivers can use
        use latency APIs.
    
        max_cstate can still be used as a boot time option and dmi override.

If anyone could give me some insight into what is meant by "latency APIs," I'd appreciate it.

---

