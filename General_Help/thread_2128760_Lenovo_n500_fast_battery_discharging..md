---
title: "Lenovo n500 fast battery discharging."
date: 2013-03-24
forum: General Help
---

### Post by kujaw on 2013-03-24
Hey guys
My battery is discharging a rate of about 20-27 W, despite of what I am doing on computer.
Laptop lasts on battery about 30-40 mins, although te battery icon shows more than two hours when it's 100%. These two hours go so quickly ;(
This is my problem since I installed Linux Mint 12 and now Ubuntu Studio 12.04.
I hope that someone will manage to help me fix this.

---

### Post by Mark Phelps on 2013-03-24
This most likely because recent Linux kernel don't have the ability to idle the processor when you're not doing much work, so it runs at nearly full power all the time -- draining the battery as a result.

You could try using Jupiter: [http://www.ubuntubuzz.com/2012/04/fix-laptop-overheating-problem-in.html]("http://www.ubuntubuzz.com/2012/04/fix-laptop-overheating-problem-in.html")

---

### Post by kujaw on 2013-03-24
It seems to be a bit more complicated. I installed Jupiter, ran "Power Saving" mode and there was no change in CPU usage, no change in temperature, no change in battery discharge, after ~30 mins the battery was nearly empty.
When I click on Jupiter's tary icon I can see that even if I change it's mode there's always written "CPU Mode: Power on Demand".
So I think that nothing changed because Jupiter fails to change modes...

---

### Post by kujaw on 2013-04-07
I noticed that after few days of using Jupiter it worked. Temperature and CPU usage is lower in "Power Saving" mode. But battery still runs for about 37 minutes. Any other advice?

---

