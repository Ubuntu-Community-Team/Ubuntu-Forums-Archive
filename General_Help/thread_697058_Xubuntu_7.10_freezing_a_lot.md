---
title: "Xubuntu 7.10 freezing a lot"
date: 2008-02-14
forum: General Help
---

### Post by Famicommander on 2008-02-14
My specs:
AMD Duron 1300mhz
256MB SDRAM
40GB IDE Hard drive
SiS 630 integrated graphics with up to 64MB shared RAM
Xubuntu 7.10 Gutsy Gibbon

The problem:
I just installed it a few days ago, and the computer freezes up within about an hour of use, and there doesn't seem to be any pattern to it. I installed from the alternate install CD, and then I had some problems with my screen resolution (I was stuck at 800x600). After I resolved those, the crashing started. I resolved it by changing the monitor settings, which allowed me to select a higher resolution.

So anyway, I've got a lot of freezing issues. This is an older computer that I added some RAM and a larger hard drive to. I was planning on giving it to my father so he could browse the internet and play Age of Empires through WINE (I've got Ubuntu running flawlessly on my own computer).

I'm fairly new to Ubuntu, so please explain everything in simple terms if you know how to help.

---

### Post by Famicommander on 2008-02-14
Forgot to mention:
It takes quite a long time for the OS to boot up. The load screen has to sit for literally 2-3 minutes before the progress bar reaches the end.

Any help would be greatly appreciated.

---

### Post by Famicommander on 2008-02-14
It's still freezing...

---

### Post by Pelham123 on 2008-02-14
Freezing or crashing? Do you have to power off and restart, or does Xbuntu 'unfreeze' and run along as normal? If Xubuntu is just being ultra-slow, it maybe worth trying this...

Switching terminals and running command 'top'. Don't know how much you know, so I'll explain:

The command 'top' is like Windows Task manager, it has a real time display showing system processes, cpu load, ram/swap usage. 

Ubuntu has 7 'virtual' full screen terminals. Next time you're logged in press <ctrl>+<alt>+F6. This will give you a text based login screen, log yourself in with usual name/pass  - you are now in a full screen terminal - and run 'top' command. If you were to press <ctrl>+<alt>+F7 you would re-appear back in your desktop. So...

Use Xubuntu as normal and when system 'freezes' hit <ctrl>+<alt>+F6 to see if any processes/apps are eating PC specs and causing a major slow down/freeze.

Just something to try/rule out as a cause. If only solution is hard reset, then I'm sorry to have waffled on :oops:

PS- to exit 'top' hit 'q'. To finish virtual terminal type 'exit'

---

### Post by Famicommander on 2008-02-14
Yeah, the only solution is to turn off the computer.

I should have mentioned that eariler.

But thanks for actually responding.

---

### Post by Jay Jay on 2008-02-16
I encountered the same issue with Xubuntu Gutsy too, In the space of 24 hours I had to power down and restart about 30 times. After I uninstalled the Flash codecs from Add/Remove programs and then used an alternative source from within Terminal, that seemed to solve it.

Many users cite the problem as related to a bug in Firefox and use Opera or Swiftweasel as a means to circumvent it.

Sorry I can't suggest more (as I gave up on 7.10 after endless grief), but I hope these suggestions help.

---

