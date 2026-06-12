---
title: "Hibernation Fails on Ubuntu 16.04 LTS"
date: 2018-02-15
forum: General Help
---

### Post by nathanieljs1541 on 2018-02-15
Hi,

So I am experiencing problems with hibernating in Ubuntu 16.04 LTS, and when I attempt to hibernate using the button in the menu located at the top of the screen (with options like shut down, log off etc.) nothing happens. If, however, I use "sudo systemctl hibernate", the screen goes blank for a second, then the log on screen appears, then the screen goes blank again, the log on screen appears once again and finally the screen goes blank and appears to have hibernated.

However, when I try and resume by pressing the power button, the system just appears to boot as if it had been shut down.

I am on a Dell Inspiron 17R 5737, Dual-booting Windows 10 and Ubuntu. I'm not sure whether the dual booting is causing the problem?

A few things I've looked at:
[LIST]
[*]/etc/default/grub contains the correct UUID for my swap partition.
[*]My swap partition is 16GB, which should be fine since I have 8GB RAM
[/LIST]

I am new to Ubuntu so there may be something I'm missing...

Thanks for any help!

---

### Post by Ralph L on 2018-02-15
I've complained about hibernation not working right for years, but nobody seems interested in fixing it.  In most systems it is disabled by default and you have to do some configuring to get it to even show up during shutdown.  And even if it does show up, restoration often doesn't work right.  I certainly wouldn't count on it to restore applications that might have critical data in them.  In my case, I have enabled Firefox to restore to the previously open windows and tabs.  This takes care of most of my needs.  Writer and Calc also seem to save my data to the last point I did entry and this solves most of my other usage problems.

Sorry about hibernate being a problem.

Ralph

---

### Post by nathanieljs1541 on 2018-02-17
Yeah I gathered that some people have found workarounds, such as uswsusp, but this doesn't seem to be working for me, since cryptsetup is finding 2 different references to the same swap partition, so it doesn't setup correctly. Hopefully something gets done about this issue eventually..

Thanks for the reply, Ralph!

---

