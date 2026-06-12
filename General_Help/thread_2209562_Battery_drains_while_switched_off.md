---
title: "Battery drains while switched off"
date: 2014-03-06
forum: General Help
---

### Post by david98 on 2014-03-06
My samsung np2705e laptop battery when fully charged drains over night when switched off at first I thought it might of been the battery but had doubts as the laptop is barely 5 month old. I tried it with a new battery just to check same thing happens. I know that laptops can use between 2-5 % battery when switched off but surely not a full charge. I also swapped hdd for a one with win 7 installed on just to check if it was the laptop it's self and nothing to do with the OS but it stayed charged over night with win 7 . Puzzled I was so I asked samsung on there website and they said it has never been reported as a problem and was not a hardware problem fat lot of good that did me. So am just wondering if anyone had any ideas what could be causing this. Opps almost forgot to say am using ubuntu 13.10. Any advice would be appreciated thanks in advance.

---

### Post by buzzingrobot on 2014-03-06
If you are shutting down and powering off, not suspending or hibernating, then, if this is Ubuntu-related, then, as a guess, perhaps a hardware device is left able to draw power from the battery even after powering down. (Admittedly, I have no idea if that is even possible.)  But, try turning off/disabling in BIOS all the components you can. (E.g., wireless card, webcam, microphone, etc.) Power off, disconnect it from the wall plug, and disconnect everything attached to the laptop: mouse, ethernet, printers, etc. In the morning if the battery has retained the charge, repeat this approach by disabling one thing at a time until/if you find the culprit.  (Then, collect the details and report a bug.)

As a control, it might be interesting to physically remove the battery overnight to see what happens.

---

### Post by david98 on 2014-03-06
There's nothing connected to the laptop everything I can disable in bios I have even usb wake up. Iv'e been trying to solve this problem for week's now to no avail. I have done everything I can think of as you mentioned not to mention searching through countless google searches. I think I will try removing the battery tonight just to check but my guess it will keep it's charge as it did with a hdd with windows inserted.

---

### Post by david98 on 2014-03-07
As I thought battery kept it's charge once physically removed overnight I have done everything I know and just cant find a reason for this to keep happening. I suppose it give's me a reason to get another laptop but this ones near enough brand new.

---

### Post by red72 on 2014-04-30
I am having the same problem.  I have been using 13.10 for six months with no issues and then in the last 2 weeks I noticed the battery draining about 15% at night.  I assume some update is causing the problem.  Any ideas?

---

