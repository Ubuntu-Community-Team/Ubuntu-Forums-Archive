---
title: "Stuck at splash screen on shutdown [LUBUNTU 17.10]"
date: 2017-11-12
forum: General Help
---

### Post by khometmibro on 2017-11-12
I installed lubuntu 17.10 on my Ideapad 110S and am having some issues with shutting down.

I try to shutdown my computer and it just stays at the splash screen. I pressed esc to see what was up and I get this:

> (1 of 2) A stop job is running for Network Manager

This message alternates to 

> (1 of 2) A stop job is running for WPA supplicant

and it just stays like that. After a few minutes it says something about "task wpa_supplicant" being blocked for more than 120 secs, and other similar error messages.




Won't shut off. I have to force a shutdown by holding the power button.

---

### Post by DuckHook on 2017-11-13
A little snooping around returns the following:

[https://askubuntu.com/questions/965856/kworker-blocked-for-more-than-120-seconds-ubuntu-17-10](https://askubuntu.com/questions/965856/kworker-blocked-for-more-than-120-seconds-ubuntu-17-10)
[https://askubuntu.com/questions/966429/a-stop-job-is-running-for-wpa-supplicant-slow-to-shut-down](https://askubuntu.com/questions/966429/a-stop-job-is-running-for-wpa-supplicant-slow-to-shut-down)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1724317](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1724317)

I don't know whether your issue is the same as these. However, you can try reverting to an earlier kernel to see if this solves the problem. If an earlier kernel works, then this reinforces a theme that I've mentioned many times before on these forums: using the latest non-LTS version is unnecessary and invites problems for most general users. Best to stick with the LTS versions. Currently, that is Xenial until Beaver debuts in April 2018. Until then, unless you have bleeding edge HW that must use the latest kernel or other unavoidable needs, an LTS version is more stable and less prone to problems.

You can check if this problem persists with a Xenial LiveUSB. If everything runs nicely in Xenial, then why ask for instability and problems with Aardvark?

BTW, instead of pulling the plug (as it were), next time, try shutting down more elegantly with REISUO. [https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

---

