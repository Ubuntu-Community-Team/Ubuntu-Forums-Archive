---
title: "Heating Related Obsession, (AMD)"
date: 2016-01-16
forum: General Help
---

### Post by hasancankaraca on 2016-01-16
Hey everyone,

I've been using Linux for one and a half years now and I enjoy every minute; however I've developed a small obsession on heating. I used Ubuntu 14.04, Linux Mint 17.1 and currently I'm using Ubuntu MATE 15.10. Maybe because my CPU and GPU are AMD I feel like my laptop always runs hot; nevertheless in idyling it hovers around 38 degrees (Mint 17.1 starts with 35 degrees and ascends to 40-41), h.264 videos -480p- in full screen -hd- around 63 (I remember Mint had 55 degrees or so), h.265 videos -1080p- around 73 degrees (Mint was 65 or above). Web browsing, Youtube videos are pretty much same, sometimes it heats up to 70 degrees (opening new tabs constantly or several open tabs and video in backround), however all linux distros have flash issues so I assume that's okay.

My question is, I know those temperatures are normal for A8-4500m CPU (Max: 100 degrees operating) however I can't stop desiring a cooler laptop; what am I missing? Should have I waited more to upgrading 15.10, should I clean my fans or an update will cool my laptop. Interestingly, the fan spins not so fast. Therefore I also assume; for system these temperatures are just fine.

My laptop model is Asus K55N-DB81. TLP and Prop. drivers are installed.

---

### Post by QIII on 2016-01-16
APUs generally run hot. remember that both the CPU and GPU are on the same die, so the heat from each is combined.  So they are designed for higher thermal loads.  That is exacerbated by the limited cooling available on a laptop.

You might see if you can blow some compressed air through the vents to clear out any dust build-up that may be there.

Your temp does not seem out of line to me for an APU.

---

### Post by hasancankaraca on 2016-01-16
Thank you so much. Probably after few updates the results will be catching up with Mint, (it's fresh install, it will settle by the time probably idk). But if you say it's all-right, maybe it's time for removing the sensors indicator from the panel :D

---

### Post by QIII on 2016-01-16
I wouldn't remove the sensor applet.  What if something really does go wrong and you don't see it?

---

### Post by hasancankaraca on 2016-01-16
I used to use Psensor actually, I look at it when I want; however libsensor just flashes to me all the time. I always feel nervous; it's like "oh! it's 65 again, why god why?". Thanks for the advice thou, it's better that i get used to it.

---

### Post by coldraven on 2016-01-17
I had an Asus eeePC 900 and after updating the BIOS the fan was much quieter. On may main laptop (HP) the heat exchanger was half choked with fluff, I had to remove the keyboard to get at it.

---

