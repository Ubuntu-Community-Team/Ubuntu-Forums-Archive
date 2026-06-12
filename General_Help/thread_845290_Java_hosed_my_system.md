---
title: "Java hosed my system"
date: 2008-06-30
forum: General Help
---

### Post by xcorvis on 2008-06-30
I'm working with a faculty member on her Ubuntu system (8.04) and she's had some serious problems installing java. She used syntaptic to install sun-java5-jdk and its dependancies. She also installed sun-java5-plugin. After that, she noticed some java errors while running matlab. When I rebooted the system, I get the brown ubuntu background and the spinning wheel mouse icon, but the system hangs at that point. Instead of the wheel spinning properly, the dot runs about 1/4 around the wheel and then stops and repeats indefinately. Restarting X or rebooting doesn't help. I can switch terminals with Ctrl-Alt-F1 and log in that way. I don't see any rogue processes that I can identify, and the logs are suprisingly blank. I've tried removing sun-java5-jdk with apt-get and dpkg but I get error messages like this:

update-mime-database: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64

I also get errors about exit status 127, and the package is not removed. (Sorry I can't cut and paste the full errors, I have to work from another computer.)

This actually happened to us last week too, but I gave up trying to fix the problem and just reinstalled. This time we noticed that the only changes had been the install of the java package, so that seems like most likely culprit.

Any ideas on how to restore the system to a usable state? That is, besides reinstalling.

Thanks for your help!

---

### Post by xcorvis on 2008-06-30
A quick follow up: There was one other thing we did between installing Java and the failed reboot, and that was add Matlab's library path to ld.conf.so. We removed that and the system is working again.

---

