---
title: "Download faster in Windows than Kubuntu"
date: 2022-04-12
forum: General Help
---

### Post by Shibblet on 2022-04-12
I have been fussing with attempting to get Skyrim running on Kubuntu.  Proton makes this no issue at all...  However, I want to Mod Skyrim, and this becomes a bit difficult in Kubuntu...   I decided to set up a small Windows partition in order to run some Windows games that do not work (the way I want) under Proton.  Regardless, this is not the issue.

The issue is that Steam downloads significantly faster in Windows than it does in Kubuntu.  I have a great 2g internet connection...  In Windows, I got about 200Mbps - 250Mbs downloads, but in Kubuntu it hovers around 18Mbps to 20Mpbs.

Here is a screenshot of my Download in Windows.  I unfortunately didn't take a screenshot of this in Kubuntu, but I did see the end results, and it's literally 10x slower...

[ATTACH=CONFIG]290277[/ATTACH]

Any ideas?

---

### Post by TheFu on 2022-04-12
Not that this helps, but 2G networks are being turned off here. [https://www.digi.com/blog/post/2g-3g-4g-lte-network-shutdown-updates](https://www.digi.com/blog/post/2g-3g-4g-lte-network-shutdown-updates)

They are 3G and above now. Also, 2G data connect speeds were definitely limited to 100**K**bps or less, so I suspect the 2G you have isn't really 2G or there are some unit differences being missed.
3G is 3 Mbps, tops. Sunset for 3G is the end of 2022 in the US.  Also, between 60-120 devices can connect at those speeds without getting in each other's way.

4G LTE was a huge change.  Peak speeds around 50 Mbps are possible and many more concurrent users (500+).  T-Mobile actually provides home routers with service connected over 4G LTE for $50/month. I know a few people with it. I haven't seen any dates for 4G end-of-service.  
[https://www.t-mobile.com/isp](https://www.t-mobile.com/isp)

Last time I was in Alaska was about 4 yrs ago and t-mobile didn't work well anywhere. It could have been that I wasn't on a monthly plan, but all my friends were on AT&T there and had the most consistent service available ... as much as any mountain areas will provide.

Anyway, how is the data connection made between the internet modem and your Linux computer?  I can't see a router connected via the same data method drastically changing due to the client OS.  Is the connection wired, wifi, USB-networking, or BT?

---

### Post by Shibblet on 2022-04-12
> **TheFu said:**
> Anyway, how is the data connection made between the internet modem and your Linux computer?  I can't see a router connected via the same data method drastically changing due to the client OS.  Is the connection wired, wifi, USB-networking, or BT?

LOL!  Yeah, maybe I should explain that!  ;-)

This is a 2.5gbps Cable Modem via Ethernet.  Same computer, same game, same Steam account.  Only (discernable) difference is the OS.

Edit:  Cable Modem with Router built-in.  Direct connection to the cable modem.

---

### Post by Shibblet on 2022-04-12
> **TheFu said:**
> Not that this helps, but 2G networks are being turned off here. [https://www.digi.com/blog/post/2g-3g-4g-lte-network-shutdown-updates](https://www.digi.com/blog/post/2g-3g-4g-lte-network-shutdown-updates)

They are 3G and above now. Also, 2G data connect speeds were definitely limited to 100**K**bps or less, so I suspect the 2G you have isn't really 2G or there are some unit differences being missed.
3G is 3 Mbps, tops. Sunset for 3G is the end of 2022 in the US.  Also, between 60-120 devices can connect at those speeds without getting in each other's way.

4G LTE was a huge change.  Peak speeds around 50 Mbps are possible and many more concurrent users (500+).  T-Mobile actually provides home routers with service connected over 4G LTE for $50/month. I know a few people with it. I haven't seen any dates for 4G end-of-service.  
[https://www.t-mobile.com/isp](https://www.t-mobile.com/isp)

Last time I was in Alaska was about 4 yrs ago and t-mobile didn't work well anywhere. It could have been that I wasn't on a monthly plan, but all my friends were on AT&T there and had the most consistent service available ... as much as any mountain areas will provide.

They're turning off 2G in Alaska as well.  4G is available near all the major cities.  Anchorage, Fairbanks, Wasilla, Palmer, etc...  The biggest problem with Alaska and Cell-Data is that there are long stretches of highway that go between the major cities.  Anchorage to Fairbanks is almost a 400 mile drive.  Once you pass the Willow/Talkeetna area (which is about 50 miles north of Wasilla... You lose Cell Data service until you get about 20 miles out of Fairbanks.  Your phone will still work, but you get no data what-so-ever.  

This is similar from Palmer to Glennallen, and Glennallen to Valdez, etc.  Basically, when you are out about 100 miles from anywhere, you have no data service.  Fortunately, you do have cell phone service.

---

### Post by TheFu on 2022-04-12
Long stretches doesn't really cover the distances. Even in Texas, we have long stretches ... but nothing like Alaska!  I spent some time in Katmai - where the brown bear population (est. 2200) was much higher than the human population (200 on busy days). 

I've driven from Anchorage to Denali, through Wasilla. Nice drive when we were there. Beautiful area and at least during tourist periods (June-Sept), there's enough traffic to be safe on that stretch.  Sent a business partner to Fairbanks in February - some UF geospacial work.  I almost felt guilty - he grew up around the equator, so cold (anything below 65 degF) isn't something he enjoys. Where I grew up, we had snowmobiles, ice fishing, and well worn winter clothing.

Anyways, how do the computers connect to the 2G service?

---

### Post by TheFu on 2022-04-12
Oooops. I missed this.   Being extra tricky with 2 separate posts. ;)

> **Shibblet said:**
> LOL!  Yeah, maybe I should explain that!  ;-)

This is a 2.5gbps Cable Modem via Ethernet.  Same computer, same game, same Steam account.  Only (discernable) difference is the OS.

Edit:  Cable Modem with Router built-in.  Direct connection to the cable modem.

2.5Gbps cable modem?  Is it DOCSIS 3.1?  Does it provide 2.5 Gbps connectivity or is this just the current MoCA standard that you speak?  2.5Gbps over MoCA is fairly standard and doesn't get in the way. I read that Motorola makes all the chips used across every vendor's product, so interoperability is perfect, regardless.  MoCA is usually seen for house networking, like powerline. Not used between houses or to the ISP. That's were DOCSIS comes in with bonded channels (35Mbps per channel real-world. 38Mbps is the theoretical max throughput per channel).  That's why DOCSIS uploads are usually 1 or 2 channels, not more and downloads are offered in channel divisible amounts.  DOCSIS 3 made channel assignments dynamic between the plant headend and the customer address.

If your computer has a 2.5Gbps NIC, there have been bad drivers for Linux for both the realtek AND intel chips used in those for about 3 yrs.  Intel denied any issues, but still released updates for their 2.5Gbps NICs that have been included in Ryzen B[COLOR="#FF0000"]5[/COLOR]50 motherboards.  Last fall, I specifically bought a B**[COLOR="#008000"]4[/COLOR]**50 instead, to avoid the Intel 2.5Gbps NIC.

Which NIC model and chip is used on Linux?  BTW, I bet transfers on your LAN have the same limits. It isn't the ISP at all.

---

### Post by Shibblet on 2022-04-13
> **TheFu said:**
> Long stretches doesn't really cover the distances. Even in Texas, we have long stretches ... but nothing like Alaska!  I spent some time in Katmai - where the brown bear population (est. 2200) was much higher than the human population (200 on busy days).

Katmai National Park is just across the ocean from Kodiak Island.  Kodiak has some HUGE grizzly (brown) bears.

> **TheFu said:**
> I've driven from Anchorage to Denali, through Wasilla. Nice drive when we were there. Beautiful area and at least during tourist periods (June-Sept), there's enough traffic to be safe on that stretch.  Sent a business partner to Fairbanks in February - some UF geospacial work.  I almost felt guilty - he grew up around the equator, so cold (anything below 65 degF) isn't something he enjoys. Where I grew up, we had snowmobiles, ice fishing, and well worn winter clothing.

I highly suggest coming to Alaska in the summer.  Sometimes the winters here can be arduous.

> **TheFu said:**
> Anyways, how do the computers connect to the 2G service?

They tend to work the same way any other computer does.  If the computer has a SIM card slot, then it works off of that.  The Cell Phone companies have SIM/USB adapters for others.  We are very limited on our data usage over the cell networks though... the primary cell companies (GCI, Verizon, and AT&T) limit you to 4gigs of "connected" data usage.  Which in my opinion is stupid... data is data, who cares if you are connecting a PC to your smart phone, or just using your smart phone... Anyway, it is what it is. 

> **TheFu said:**
> Oooops. I missed this.   Being extra tricky with 2 separate posts. ;)

Good plan, I'll combine these posts.  ;-)

> **TheFu said:**
> 2.5Gbps cable modem?  Is it DOCSIS 3.1?  Does it provide 2.5 Gbps connectivity or is this just the current MoCA standard that you speak?  2.5Gbps over MoCA is fairly standard and doesn't get in the way. I read that Motorola makes all the chips used across every vendor's product, so interoperability is perfect, regardless.  MoCA is usually seen for house networking, like powerline. Not used between houses or to the ISP. That's were DOCSIS comes in with bonded channels (35Mbps per channel real-world. 38Mbps is the theoretical max throughput per channel).  That's why DOCSIS uploads are usually 1 or 2 channels, not more and downloads are offered in channel divisible amounts.  DOCSIS 3 made channel assignments dynamic between the plant headend and the customer address.

The cable modem is a ["Sagemcom Fast3896U."]("https://mediacomcc.custhelp.com/euf/assets/documents/modem%20user%20guides/sagmecom_fast3896_datasheet.pdf")  It has 3-1G Ethernet ports, and a 1-2.5G Ethernet port, which I use for my PC.  Everyone else in the house uses Wi-Fi.  The other three ports run my TV, and NAS...  One is left open for the kid to update his XBox when he comes to visit.

> **TheFu said:**
> If your computer has a 2.5Gbps NIC, there have been bad drivers for Linux for both the realtek AND intel chips used in those for about 3 yrs.  Intel denied any issues, but still released updates for their 2.5Gbps NICs that have been included in Ryzen B[COLOR="#FF0000"]5[/COLOR]50 motherboards.  Last fall, I specifically bought a B**[COLOR="#008000"]4[/COLOR]**50 instead, to avoid the Intel 2.5Gbps NIC.

This makes sense.  My computer is a ["Minisforum HX90."]("https://store.minisforum.com/products/hx90")

> **TheFu said:**
> Which NIC model and chip is used on Linux?  BTW, I bet transfers on your LAN have the same limits. It isn't the ISP at all.
I believe it's an "Intel i225-V."

---

### Post by Shibblet on 2022-04-13
Oops... I see the confusion...

> **Shibblet said:**
> I have a great 2g internet connection...  In Windows, I got about 200Mbps - 250Mbs downloads, but in Kubuntu it hovers around 18Mbps to 20Mpbs.

What I meant was that I have a Cable Modem that does 2Gbps... Not to be confused with 2g Cell Data.

My bad...  :lolflag:

---

### Post by TheFu on 2022-04-13
> **Shibblet said:**
> I believe it's an "Intel i225-V."

That's the problem Intel NIC.  You are doing well to have it work at all, based on my reading.  What others in these forums ended up doing was to spend $25 and get an Intel PRO/1000 or i210/i211 NIC to use until driver support for the i225 works properly.

The 2G vs 2Gbps confusion nailed it. I was confused because we do have 4G LTE here and lots of people use it for their home internet.
In the early 2000s, my job provided me with a 3G adapter for my laptop.  I used it all over the country AND when working from home. It was as fast as my cable modem at home for 99% of the use patterns.  Back then was when I started telecommuting 2 days a week.

I haven't been to Kodiak island, but have friends that work at a space company with launch facilities located there.  Spent a little time at Brooks Lake a few years ago.  Brown bear encounters were a daily occurrence.  The first thing after getting off the 1954 float plane from King Salmon was bear school.  That was 90 minutes of how to behave, where and how to keep food (bears are driven by their noses like bloodhounds) and get along with bears.  Still remember walking out the front door of the cabin while brushing my teeth and seeing a 600 lb bear about 10 ft away walking on the same path we used. It was very late July.  Also, when we arrived, there were 4 bears walking between the plane and shore.  The 6 other passengers on the plane didn't notice and neither did the camp staff or pilot.  I happened to look out the window and refused to get off the plane with so many bears 15ft away.

See my attached photo. The boards in the lower left corner ... that's from the plane to the shore.  Clearly, I'm not exaggerating the distance for encounters.  So many others happened.

---

### Post by ActionParsnip on 2022-04-13
What speed does
```

sudo lshw -C network

```
Show

---

