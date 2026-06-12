---
title: "Suspend doesn't work properly"
date: 2014-08-29
forum: General Help
---

### Post by Marcel_Moosbrugger on 2014-08-29
Hey guys,

Recently I installed the new version of ubuntu (14.04) on my new thinkpad. Since the beginning I couldn't get the suspend-mode to work properly.
The problem appears regardless of how i trigger the suspend mode. (closing the lid, via mouse-click or via terminal)

The behavior of my suspend mode is the following: The screen goes black and the sleep-mode light on my notebook begins to toggle between light and dark, so far so good.
But then the notebook seems to start working even more. The fan begins to spin faster etc. Moreover I can't get out of the suspend mode again. I can press and push whatever I want, the screen stays dark andied
the sleep-mode light keeps toggling.

I am now searching for a solution for two days now and tried the following fixes (which all had no effect): Switched to the proprietary driver of my graphics card, installed uswsusp, installed vbetool,
created the 20_custom-ehci_hcd file (followed this tutorial [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug))

I am running out of ideas. I really hope you guys can help me out.
My system is: Lenovo Thinkpad E540 with an NVIDIA GT740M and an Intel i7 4702 MQ

Thanks in advance
marcel

---

### Post by Marcel_Moosbrugger on 2014-08-31
For anyone who suffered from the same problem:
I managed the kind of fix it. After a little bit more researching i got to this bug report:
[https://bugzilla.kernel.org/show_bug.cgi?id=80351](https://bugzilla.kernel.org/show_bug.cgi?id=80351)

So the bug i mentioned is a problem in the BIOS. I managed to get suspend working with disabling USB 3.0 in the BIOS. I'll leave it like that till there is a BIOS-update which fixes the issue

---

