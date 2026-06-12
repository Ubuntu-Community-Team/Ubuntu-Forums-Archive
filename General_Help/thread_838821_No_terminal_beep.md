---
title: "No terminal beep"
date: 2008-06-23
forum: General Help
---

### Post by anlag on 2008-06-23
I cannot get my gnome-terminal to output simple beeps. The main purpose would be activating notifying beeps in irssi, my IRC client. I'm rather certain I've set the program's parameters correctly, as I can get the 'visual beep' as available in System->Preferences->Sound. I also however tried installing the 'beep' program from the Ubuntu repository, and it runs without complaining but no sound can be heard.

I have also checked in the terminal settings as well (Edit->Current profile->General) that "terminal bell" is indeed checked.

Might the PC speaker device simply not be loaded? Found something in a search, which also I'm sad to say did nothing:

anlag@casper:~$ modprobe -l pcspkr
/lib/modules/2.6.24-19-generic/kernel/drivers/input/misc/pcspkr.ko
anlag@casper:~$ modprobe pcspkr
anlag@casper:~$ beep


Any ideas?

---

