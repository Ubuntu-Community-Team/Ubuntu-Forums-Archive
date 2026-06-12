---
title: "50%+ battery drain while in suspend"
date: 2024-05-14
forum: General Help
---

### Post by currentshaft on 2024-05-14
932

---

### Post by currentshaft on 2024-05-31
2p

---

### Post by lads on 2024-08-09
I am having this issue with an Asus Vivobook with the i7 processor. In my case it looks like only the screen is powered down on suspend, even though it is set to **deep** mode.

There is [a post at AskUbuntu]("https://askubuntu.com/q/1517978/177437") reporting the same problem on an HP Pavilion with an i5 processor. This seems to be indeed a software issue and rather widespread.

---

### Post by ne29914 on 2024-08-09
10%/hour doesn't seem alarming to me.
If you want to go lower, you'll have to explore Hibernate.

---

### Post by TheFu on 2024-08-10
The different P-states for different CPUs and motherboards aren't always well supported in the kernel.  I remember reading about an issue with AMD CPUs recently.  Thought it was a fix for Ryzen 3xxx series CPUs.  Perhaps not: [https://www.phoronix.com/news/Linux-6.11-Lands-EMR-EPP-Update](https://www.phoronix.com/news/Linux-6.11-Lands-EMR-EPP-Update)  My memory seems to be failing.

Intel generally has better power management for laptops and usually with an intel CPU/MB that is a few years old.  Reverse engineering kinda sucks.  I expect to get a new-to-me 11th-gen Core i5 in a few days. I'll definitely try using standby along with whole drive encryption, assuming I can get passed the Optane and Xe GPU issues that are expected.  I haven't used any laptop since pre-COVID times.

Don't get me wrong. My desktops are all Ryzen 5xxx boxes. Intel just wasn't competitive at the time. Great systems, especially the iGPUs from AMD.

For a few years, I had a Toshiba i3-5015U that used standby every night just fine.  I'd leave it unplugged for 5 days, no issues. It would boot back to my exact location. I only use standby at home. If the computer is being moved outside the building, I fully shut it down to the LUKS encryption protects the data.

Also have an Asus Vivobook i5-8250U that uses standby every night. That also works fine ... er ... except the keyboard which broke and became useless. Worse, the keyboard sends random keystrokes. It was a used laptop and replacing the keyboard was going to cost over 50% of the total worth of it, so I never bothered. I've learned my lesson on keyboards.  Lenovo or Dell. Accept nothing less (crap).

You've probably already seen this: [https://www.reddit.com/r/linux/comments/x8n93s/guide_how_to_fix_excessive_battery_drain_on/](https://www.reddit.com/r/linux/comments/x8n93s/guide_how_to_fix_excessive_battery_drain_on/) but for the lurkers.

---

### Post by currentshaft on 2024-08-10
.

---

