---
title: "Ryzen 5 or Core i5"
date: 2020-03-10
forum: General Help
---

### Post by 11081987-joselu on 2020-03-10
Hi everyone):P

I'm renewing my laptop and I've already seen one I like. The laptop is an Acer Aspire 515-43. The hardware is: processor AMD Ryzen 5 3500U, SSD 512GB, Radeon vega 8 graphic card and Wi-Fi 802,11ac (Wi-Fi 5). The thing is, I've read a lot on the Internet that the compatibility between ryzen and Linux gives quite a few problems, and the graphics too. I also have the option to buy the same laptop with an Intel Core i5 1035G1 processor, Intel UHD graphic card, and Wi-Fi 802.11ax (Wi-Fi 6) but with a considerable price hike. Money is not a "problem", but I have to say that the use I'm going to give it is simple. For compatibility I'm almost sure that the Intel will not give me problems, but I would like to know your opinion about the Ryzen. Both, Intel and Ryzen do not have Windows installed, they come with FreeDOS.

Is Ryzen really going to give me trouble? Is it worth paying more for the same laptop with Intel? Which one would you choose?

Greetings and thanks for your time;)

---

### Post by ipv on 2020-03-10
> **11081987-joselu said:**
> For compatibility I'm almost sure that the Intel will not give me problems

you answered your own query. 

> **11081987-joselu said:**
> Both, Intel and Ryzen do not have  Windows installed, they come with FreeDOS.

excellent, just the way i like it.

> **11081987-joselu said:**
> Is it worth paying more for the same laptop with Intel?

if i was you i would.

> **11081987-joselu said:**
> Which one would you choose?

have been buying, recommending & using desktops & laptops since 20 years with intel inside & intel has never failed me on any machine.

---

### Post by Frogs Hair on 2020-03-10
According to PassMark the i5 benchmarks only slightly higher than the AMD. I only have experience with older AMD CPUs and they have been no problem with Linux. I don't know how AMD graphics are running currently with Linux being a Nvidia user. I have an i5 on my laptop as well.

---

### Post by QIII on 2020-03-10
Just a note ...

AMD is a member of the Linux Foundation.

Brand loyalty can be blinding.  The fact is that you should choose hardware that meets your specifications -- whatever the brand.

---

### Post by 11081987-joselu on 2020-03-10
Thanks ipv, I appreciate your answer ;) greetings and have a nice week!!

---

### Post by 11081987-joselu on 2020-03-10
Thanks QIII, greetings and have a nice week!! :-)

---

### Post by CatKiller on 2020-03-10
> **11081987-joselu said:**
> The thing is, I've read a lot on the Internet that the compatibility between ryzen and Linux gives quite a few problems,

Not at all.

> and the graphics too.

This is the bit.

Intel have a bajillion dollars and spare engineers just down the back of the sofa. They can afford to get all their ducks in a row long before they release new hardware. Nvidia also have quite a lot of money, and their proprietary driver has an awful lot in common with their well-funded Windows driver, so they can have their driver ready to go for all distributions straight away, too. AMD can't afford that. They'll generally release some largely functional code pretty soon after they release their hardware, which then needs to trickle down to all the distributions as they get released, generally being polished up on the way. Older AMD graphics hardware on standard releases is perfectly fine - works well, has most of the kinks straightened out - but new AMD graphics hardware needs really new software. That means that you'll need to use 19.10 or (the not-yet-released) 20.04, or 18.04 with the Hardware Enablement Stack and a PPA that provides newer Mesa.

---

### Post by QIII on 2020-03-10
I've used AMD graphics for years, including back before AMD bought ATI.  I've used Intel graphics and NVIDIA.  I've had good luck with all of it.

AMD hardware is well supported.  AMD is a member of the Linux Foundation.  The issue with ***any OEM*** is that the very newest hardware may not immediately be support by Linux.

---

### Post by CatKiller on 2020-03-10
> **QIII said:**
> AMD is a member of the Linux Foundation.

So are Intel, Nvidia, and Microsoft. The broader point of your post holds, but this specific part isn't a factor.

---

### Post by QIII on 2020-03-10
> **CatKiller said:**
> So are Intel, Nvidia, and Microsoft.

I didn't say they weren't.  The point of specifying the membership for AMD is to counter the nonsensical warning about AMD Ryzen and Linux.  That's plain FUD.

---

### Post by ipv on 2020-03-11
> **11081987-joselu said:**
> Thanks ipv, I appreciate your answer ;) greetings and have a nice week!!

the thread is marked as solved but what is the verdict ;)

> **CatKiller said:**
> Intel have a bajillion dollars and spare engineers just down the back of the sofa. They can afford to get all their ducks in a row long before they release new hardware.

from a customer's point of view i would see that as a plus.

---

### Post by mastablasta on 2020-03-11
> **ipv said:**
> 
from a customer's point of view i would see that as a plus.

it is. on the other hand their mitigation of security bugs reduced the CPU power down to levels below or same as those of AMD. And AMD still has better GPU chips. i think i will go with AMD CPU when i get a (planned) laptop. you just get a lot more for a lot less. at least here. difference between similary powered AMD and intel is almost 100 EUR

---

### Post by TheFu on 2020-03-11
I'll chime in w/ an opinion too.

For a desktop not used specifically by a full-time gamer, AMD CPUs have the processing edge based on "value" - price/performance. Don't think there is any question about that.  I have both Intel and AMD systems here.  Today, I'd buy a Ryzen, no question.  My last build a little over a year ago was a Ryzen 5 2600 (6 cores/12 threads).  Very happy. Extremely stable and fast.

For a laptop, there are just some things that Intel does a little better than AMD.  Power use. Heat generation. Integrated GPU drivers. Last year, I replaced a Core i3-5015U laptop w/ a newer Core i5-8250U in a used Asus laptop. That's an 8th generation CPU. Everything works except the fingerprint reader (which I would never use due to security considerations).  For me, the 8 hr battery, Intel GPU, where key parts of the decision.  I specifically didn't want any discrete GPU that would make the battery life 2-4 hrs.  Standby works perfect every night and every morning.  My only complaint is about the keyboard quality.  Seems that only Dell makes quality keyboards.  Not Toshiba, Acer, Asus, HP.

There are some specific Intel CPU families which have been hit w/ stability problems. Think they were 5-7th gen versions, but do your own research.  I've not come across the reported issue on any of my systems. My sample size is tiny.

If you don't need long battery life, then Intel becomes less of a need and other concerns would take higher priority. Only you know.

---

### Post by him610 on 2020-03-11
> Ryzen 5 2600 (6 cores/12 threads). Very happy. Extremely stable and fast.

Could not agree more with a recent build just last month. I have been very satisfied with the Ryzen 5 2600 APU.

---

### Post by mastablasta on 2020-03-12
HP has good keyboards but only on some models. I have Fujitsu at work (business model). also descent keyboard.

my kid wanted to buy a PC and i saw sale after new year. Ryzen 7 was more than half price. but the 2nd gen. it good enough for the use. so we took one without AMD GPU, added descent Nvidia, used some parts (that were relatively new) from the old PC  to it and everything just worked out of the box. he is very happy as he got a really powerful PC for 500 EUR. it was overkill if you ask me but it is what he wanted and saved the money for and i saw this opportunity to build it.

---

