---
title: "4K Support Issue"
date: 2021-08-13
forum: General Help
---

### Post by liamgorham on 2021-08-13
Hi Everyone, 

Hopefully one of you can help, i've recently installed on a USFF HP Elitedesk G1 Ubuntu which is running fine for the most part, however unlike the Windows 10 previously theres no options that i can find to set 4K 30Hz on it. Due to the DP limits you would have to lower it to 30Hz in Windows but it would then run 4K no issue. Theres options to set 30Hz but it refuses to show anything higher than 1920x1080 - I tried adjusting the monitor.xml file to the 4K resolution and 30Hz > restart but it had the same result after restarting. i've tried via xrandr on terminal too but it doesn't seem to like it there either (might be doing it wrong though) 

Sadly there are no display apps either on the software store to set custom resolutions that i can find, if theres any 3rd party apps that would be ideal! 

Many thanks in advance for the help! 

Liam Gorham

---

### Post by sudodus on 2021-08-13
4K graphics works for me in 18.04.x LTS as well as 20.04.x LTS so it should work for you too with an nvidia chip. If I remember correctly, it works both with the free Linux driver nouveau and a proprietary nvidia driver

I am using nouveau now but I have an older nvidia chip than yours, *if* yours matches what I find via the internet. Please tell us: What is the graphics chip/card (brand name and model)? Someone [else] may have detailed knowledge about how your graphics chip/card works in Linux.

By the way, is another monitor connected at the same time? In that case *maybe* the resolution of that monitor will limit also what is sent to your 4K monitor.

---

