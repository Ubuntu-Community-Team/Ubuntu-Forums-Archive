---
title: "How to determine ATI driver version?"
date: 2007-10-18
forum: General Help
---

### Post by LeBurt on 2007-10-18
Well, they warned me...

I just installed Gutsy even though the release notes said there was a problem with some ATI cards (mine a Radeon 9600). I figured it wouldn't apply to me... yeah right!

So after searching and searching, I'm still stuck. Here's my problem, sequentially:

1. The normal "ati" driver works fine but they say I need to enable the "fglrx", 3D-accelerated, restricted driver to have the fancy 3D desktop effects;
2. The "fglrx" driver is the one that has a problem: screen stays dark on boot;
3. I tried some of the suggested fixes (like editing /etc/X.11/xorg.conf) but nothing worked;
4. I reverted back to the 2D "ati" driver and started looking for answers;
5. Some people say that I need the "fglrx" v8.42 driver from ATI (which isn't out yet...)
6. This prompted me to check which version of "fglrx" I have.

And that's where I got stuck.

So, after this long preamble, my question is: how, generally speaking, do you determine the version of a driver that is on your hard drive, but not in use? More specifically, how do you do this for the "fglrx" driver for my ATI card?

By the way, if I try fglrx-info at the command prompt, it doesn't give me the info I want, just the info about the "ati" driver currently in use.

---

