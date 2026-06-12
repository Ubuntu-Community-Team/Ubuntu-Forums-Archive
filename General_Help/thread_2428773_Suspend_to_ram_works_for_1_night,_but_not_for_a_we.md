---
title: "Suspend to ram works for 1 night, but not for a weekend?"
date: 2019-10-09
forum: General Help
---

### Post by ronald10 on 2019-10-09
Ubuntu 18.04
Asus Zenbook 
Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz


When i suspend my laptop to ram it wakes up fine, if it only last a night. When ever it takes longer (say a day and a half,a weekend) it is not suspended anymore (no flashing led) and performs a full (re)boot when turned on.


Now i would understand this if the battery would be empty, but when this happens the battery is a say 46%, more then enough to me.


Any hints where to look?

---

### Post by Impavidus on 2019-10-09
Do you mean the battery is at 46% when you suspend or when you restart?

If you can determine how much battery charge your laptop uses during a 10-hour suspend, you can extrapolate how long the battery should last. On my laptop, I once estimated it should last about 40 hours. But I never suspend longer than about 5 hours. Keep in mind the battery indicator isn't always very linear.

---

### Post by ronald10 on 2019-10-10
What i mean with the 46% is that after my laptop stopped during an long suspend, then after boot it shows 46%. Meaning it was far from empty when it actually "died".

---

### Post by ronald10 on 2019-10-14
So as a test, this weekend i took the laptop home and left it suspended on AC power. This worked, laptop was still suspend on monday morning. So the "bug" only shows when suspend on battery.

---

### Post by krjinn on 2019-10-23
I have the same issue. When suspended in battery mode, after a number of hours (the correct amount I could not specify) my laptop wakes by itself.
I'm using Xubuntu 19.10

I just solved this by not suspending anymore, but if someone knows how to fix this, it please do.

---

### Post by GhX6GZMB on 2019-10-24
The battery management (BM) on most laptops is designed for medium/high current draw and will only work reliably in this mode.
If you do a long-time "suspend to RAM", say, 100 hours, and your battery is 3200 mAh, the measured discharge will only be 32 mA, which is very difficult for the BM to measure.
Your battery is empty, but the BM still thinks it's half full.
"Suspend to RAM" is only intended for short-term use.

---

