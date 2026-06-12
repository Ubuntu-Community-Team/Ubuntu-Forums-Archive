---
title: "Xorg doesn't start. Log says &quot;Caught signal 7 (Bus error)&quot;"
date: 2014-10-07
forum: General Help
---

### Post by Fallingwater on 2014-10-07
I installed Ubuntu with Mate as the GUI for a friend, the computer is an Asus S301L. It worked fine for a while, but then he said that it was failing to boot. He says he didn't do anything other than updating the system as requested by the update manager.

What happens is that the starting screen - the one with all the [OK] statuses - flashes a few times, then I get a text login prompt and a line saying the crash report daemon has been started.

I can login in text mode, and reading Xorg.0.log I find that error.

If, at this point, I manually do startx, the GUI does start and autologin, but it's all broken - the panel doesn't appear, for instance, and alt+f2 does nothing. I get a desktop with the various icons the user put there (mainly images and pdfs). I can open them, the relevant apps do start, but I can do nothing else.

fsck comes up clean, by the way.

Any ideas how to solve this? I'd really rather not have to nuke from orbit. I Googled, but I can only find old bug reports. I did an apt-get dist-upgrade from console in case there were broken packages; it did its thing, but it solved nothing.

[dmesg]("http://pastebin.com/N2uSXPSh"), [Xorg.0.log]("http://pastebin.com/mKteVZuZ"). There is no xorg.conf.

---

