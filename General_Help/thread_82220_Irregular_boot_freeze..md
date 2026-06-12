---
title: "Irregular boot freeze."
date: 2005-10-26
forum: General Help
---

### Post by Scott Robinson on 2005-10-26
I have been having an unreliably reproducable boot-up issue. It occurs at least one, often times more, per day and thus is very annoying.

Ubuntu loads to the GDM / login splash screen. The boot process continues in the background. If I login, then the screen will turn brown as per normal before the GNOME/Ubuntu splash and session load appears. However, the session load will never start. It remains frozen and stuck.

If I switch to the text virtual terminals, I found out the init process hasn't completed. The boot process apparently is stuck on loading postfix. I'm unable to open a shell (as the gettys aren't started) to find out what/where the boot process has frozen.

I think the core problem is whatever is stopped the postfix load is also stopping the login process. If I never login, and switch VTs, postfix is locked/still locks regardless. The events are not, directly, related.

Any ideas as to the problem, or even how to begin diagnosing it?

---

