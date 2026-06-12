---
title: "Ubuntu PC has slow network speeds"
date: 2016-08-01
forum: General Help
---

### Post by ChristmasPi on 2016-08-01
My Ubuntu 14.04 laptop has very poor network speeds when connecting to my ISP fiber network.

Before I call the ISP, is there any troubleshooting that I can do on the laptop to ensure that this is not a local issue?
I seem to remember back in the XP days, I could hover my mouse arrow over my network connection and I could see that I was connected at 10/100.  Is there anything similar on Ubuntu to see what network speed this laptop is connected at?

---

### Post by banceu_sergiu_ione on 2016-08-01
You can do a right click on Network icon and check the speed under Connection Information. This is the same as you was recall form XP.
You can check if your enthernet provider have any speed tester on its own website for more information. 
Or you can start download a big file and check the download speed  in system monitor under recourses. In this case the speed is related to the server you download from.
Or run a test on speedtest.net
For more information you can check the [Ubuntu documentation related to slow speed]("https://help.ubuntu.com/lts/ubuntu-help/net-slow.html")

---

### Post by ChristmasPi on 2016-08-01
> **banceu_sergiu_ione said:**
> You can do a right click on Network icon and check the speed under Connection Information. This is the same as you was recall form XP.
You can check if your enthernet provider have any speed tester on its own website for more information. 
Or you can start download a big file and check the download speed  in system monitor under recourses. In this case the speed is related to the server you download from.
Or run a test on speedtest.net
For more information you can check the [Ubuntu documentation related to slow speed]("https://help.ubuntu.com/lts/ubuntu-help/net-slow.html")

I took a look at the link speed information that you offered above and here is what I see:

1.  Under connection information, my speed shows as 300 Mb/s.
2.  When i run a speed test, my download speed is 60.97 Mbps
3.  My ISP guarantees me a rate of 200 Mb/s.

Since I'm only getting a speed of 60 Mpbs instead of 200 Mb/s, where could the issue lie, is it with the ISP, especially because under connection infroamtion, my speed shows as 300Mb/s?

Thank you

---

### Post by kurt18947 on 2016-08-01
What I suspect you'll find if you get your ISP involved is that they'll only want to work with Windows, If you're in the U.S, all their 'tools' will be Windows only. I assume you're using a wired connection? Wireless can have its own issues through no fault of the ISP. I'm using Ubuntu-Gnome but I suspect Ubuntu-unity would be similar. I left-click the network icon, left-click the connection name then network settings. "Wired" then the little cog thingy in the lower right corner.

---

### Post by Bucky Ball on 2016-08-01
My first question: What speeds is your router capable of?
And secondly: Have you ever achieved speeds of 300Mbps with your current hardware running any release of Ubuntu (or Windows)?

When an ISP gives you a download speed, in my experience, subtract about a fifth to a quarter of that and you'll be getting close to realistic. That is still nowhere near what you're getting. 

The other question is, and you can't really answer this one: are the servers you're pinging capable of pinging back at 300Mbps? You are limited by a number of factors here and not solely the speed the ISP is telling you you are likely to expect. 

I use the [Ookla]("http://www.speedtest.net/") speed test which seems to be the most reliable I have found.

---

### Post by Bucky Ball on 2016-08-01
My first question: What speeds is your router capable of?
And secondly: Have you ever achieved speeds of 300Mbps with your current hardware running any release of Ubuntu (or Windows)?

When an ISP gives you a download speed, in my experience, subtract about a fifth to a quarter of that and you'll be getting close to realistic. That is still nowhere near what you're getting. 

The other question is, and you can't really answer this one: are the servers you're pinging capable of pinging back at 300Mbps? You are limited by a number of factors here and not solely the speed the ISP is telling you you are likely to expect. 

I use the [Ookla]("http://www.speedtest.net/") speed test which seems to be the most reliable I have found.

---

### Post by ChristmasPi on 2016-08-01
> **kurt18947 said:**
> What I suspect you'll find if you get your ISP involved is that they'll only want to work with Windows, If you're in the U.S, all their 'tools' will be Windows only. I assume you're using a wired connection? Wireless can have its own issues through no fault of the ISP. I'm using Ubuntu-Gnome but I suspect Ubuntu-unity would be similar. I left-click the network icon, left-click the connection name then network settings. "Wired" then the little cog thingy in the lower right corner.

The results I provided above were from my wireless PC, but I have tried the same from a wired PC and my speed test is roughly 80 Mpbs, but again, no where near what is promised.

---

### Post by kurt18947 on 2016-08-06
> **Bucky Ball said:**
> My first question: What speeds is your router capable of?
And secondly: Have you ever achieved speeds of 300Mbps with your current hardware running any release of Ubuntu (or Windows)?

When an ISP gives you a download speed, in my experience, subtract about a fifth to a quarter of that and you'll be getting close to realistic. That is still nowhere near what you're getting. 

The other question is, and you can't really answer this one: are the servers you're pinging capable of pinging back at 300Mbps? You are limited by a number of factors here and not solely the speed the ISP is telling you you are likely to expect. 

I use the [Ookla]("http://www.speedtest.net/") speed test which seems to be the most reliable I have found.

You might take a look at openspeedtest.com or speedof.me.  One less reason to have to uncage Flash and openspeedtest in particular seems pretty accurate. 

Edit: I see where speedtest.net has a Flash-free beta version available.

---

