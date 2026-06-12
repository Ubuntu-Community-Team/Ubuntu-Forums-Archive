---
title: "Live OS Question"
date: 2020-05-08
forum: General Help
---

### Post by majukic on 2020-05-08
Hi
I recently made Xubuntu my main OS on my laptop and would like to trial Ubuntu on a Live OS USB on the same computer.
It seems in the first instance that running a Live Linux OS works fine using a Linus OS USB in a Windows OS environment,  When I run the Linux USB in a Linux OS it doesn't work.  Is there a specific boot creator tool that I can use that's specific for Live Linux OS on a Linux computer or am I missing something?

---

### Post by CatKiller on 2020-05-08
You don't run the live USB in any environment, you just boot from it.

---

### Post by majukic on 2020-05-09
thanks i have booted under legacy boot and it still just bypasses and loads the Xubuntu OS, but from a windows OS works every time

---

### Post by guiverc on 2020-05-09
I boot 'live' environments many times a week, however the way it boots can vary from machine to machine. On some boxes just inserting the thumb-drive with my chosen system (eg. Xubuntu) boots straight away, however on others it requires me to hit a key before it'll be recognized. The key I need to press varies on BIOS/UEFI setup, which can be F9, F2, F10, F12, <blue> <thinkvantage> etc (the key being machine specific)

How it appears also differs too, eg. the menu is rather pretty on some boxes, but the same OS/thumb-drive menu appears as if it's a boring `grub` menu on others  (ie. machine specific).

You're describing how it appears on one lenovo thinkpad I don't like... I have to be so very quick on that machine in pressing the key (*and remember what key it is*), if I'm not quick enough it boots the installed Xubuntu 18.04 LTS on my box too.

---

### Post by majukic on 2020-05-09
I choose the F2 key on mine so that i can boot directly from USB, fairly straightforward on my machine.  The problem for me that it doesn't boot into the Linux OS.  I use Rufus, Universal USB Installer, Linux Live USB Creator etc and it still fails to load

---

### Post by guiverc on 2020-05-09
The first thing I do when I boot a newly written 'live' system to a thumb-drive is boot it on a box & use the self-validation option ("*Check disk for defects*"). On the latest 20.04 series, this option is automatic rather than an optional item so it runs automatically.

If however I cannot get that run, I eject the thumb-drive, and try booting it on another box and run it there. If it fails to boot on the second box, my assumption is the write of the ISO to thumb-drive was faulty, and I thus re-write it and try again. If it fails again, I test the media by trying to write using another machine (different environment) and if it fails there, the thumb-drive is likely to be thrown in the bin to my right (it's clean, and if I decide my method was flawed I'll retrieve it before I empty the bin on *trash-day*)  I'd then use different media (ie. different thumb-drive).

Your description hasn't verified the ISO write to media (which for some reason I find the weakest link), nor if you validated the ISO before it's write to media (ie. [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0))

---

### Post by sudodus on 2020-05-09
There is a lot of good advice in the posts by guiverc.

I will add some links, that may help with a few more tips.

[help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Why Doesn't a Bootable USB Boot](https://askubuntu.com/questions/1190764/why-doesnt-a-bootable-usb-boot/)

---

### Post by majukic on 2020-05-09
thanks alot guys will follow advice, cheers

---

