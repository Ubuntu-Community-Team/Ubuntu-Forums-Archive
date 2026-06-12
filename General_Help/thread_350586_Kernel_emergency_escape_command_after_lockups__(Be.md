---
title: "Kernel emergency escape command after lockups?  (Beryl lockups)"
date: 2007-01-31
forum: General Help
---

### Post by Yfrwlf on 2007-01-31
Yes, Beryl is only verison 1.99.2 or something, so I expect it to crash now and then.  What I don't expect though is for the Linux Kernel, one of the most stable kernels that I know of, to not allow you to kill whatever is causing a lockup, as long as the kernel itself is still running.

Since I've always been able to continue moving my mouse if Beryl does crash I assume the kernel hasn't panicked, but CTRL-ALT-F* doesn't work is the problem.

Since there is no place on [www.kernel.org](www.kernel.org) to ask about this that I can find, I'm asking here.  Shouldn't there always be a back door if things get really bad??  Why won't CTRL-ALT-F* always work?  Sure, if the kernel itself crashes then that's another story, but if it doesn't appear to have, why isn't there always a way out?  Sometimes just an app crashes, sometimes it takes down X too (but much more rarely), and sometimes the crash prevents you from even being able to leave X.  Maybe the kernel *is* locked?

Does anyone have any opinions or ideas about this and any other special keys that could possibly bail one out of such a situation without a reboot?  I've tried some weird ALT-SysRq-K commands before but those don't seem to ever work.

I'd really like to be able to tell my friends "the Linux kernel is TOTALLY crash-proof" but I can't, just that it's extremely stable and only if you're doing things like messing around with Beryl have I ever completely screwed it up ;)

---

