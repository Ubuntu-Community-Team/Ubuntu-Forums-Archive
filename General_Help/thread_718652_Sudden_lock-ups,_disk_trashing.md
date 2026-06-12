---
title: "Sudden lock-ups, disk trashing"
date: 2008-03-08
forum: General Help
---

### Post by gilgongo on 2008-03-08
I've recently installed Gutsy, and it's been fine until the other day. I was writing an email in Evolution, when suddenly the disk started thrashing like hell, and the whole machine then started to lock up (mouse moving very slowly, windows not responding). The Evolution window also greyed out.

It's happening about once a day now. Usually when I'm not doing much. Just now I had a Firefox window open (as well as Evolution), clicked a link in it, and bang - the disk kicks off big time and I have to eventually hit CTRL+ALT+backspace and kill the power.

The only thing that I can think of that's changed is that I received an Evolution package update the other day, and ever since then things have been way bad.

Has anyone else experienced this? 

If it gets really bad I'm going to have to migrate to Thunderbird or something to see if that helps.

---

### Post by gilgongo on 2008-03-08
A little more investigation (it just happned again when I opened Evolution after a reboot) shows tha Xorg is flying out of control: eating up memory and swap exponentially until the system grinds to a halt.

What is going on? I'm not running Desktop Effects (I suspected Compiz), so it's not that I don't think. What else could be the problem?

---

