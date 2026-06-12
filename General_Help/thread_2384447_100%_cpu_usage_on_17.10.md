---
title: "100% cpu usage on 17.10"
date: 2018-02-07
forum: General Help
---

### Post by kevinorourke2008 on 2018-02-07
Hi Guys, i was wondering if anybody else was having this problem? When i switch my computer on I am getting 100% cpu usage even before opening any software. I'm running a Toshiba satelite, intel® Celeron(R) CPU 1005M @ 1.90GHz × 2, 3.7 gig memory, 64 bit and 4 gig ram. Oh and ubuntu 17.10. 
Ive found that running the internet I'm starting to get mouse judder and sticking. Never used to happen under the older version of ubuntu. Any suggestions?


cheers kev.

---

### Post by Impavidus on 2018-02-07
Try and find out which program is responsible for the cpu use. For example, use the terminal program **top**.

---

### Post by kevinorourke2008 on 2018-02-07
Hi, I have foumd it. I looked and found that "boinc" has been running in the background using all available CPU capacity available. Many thanks for the help.

---

### Post by raleigh3 on 2018-02-08
I would uninstall boinc.

---

### Post by kevinorourke2008 on 2018-02-09
Hi Raleigh3,
I use boinc to contribute to processor sharing to help fight disease such as AIDS, Malaria, etc etc. What i have discovered in the settings in Boinc is the cpu % thati it can use at any one time. I have set this to 50% now, but the default is 100%. anyway, the cpu usage is now sitting nicely at 50% when no other program is running. The mouse doesnt freeze or stutter any more. I think I've solved this one with the help of members.

Kev.

---

### Post by raleigh3 on 2018-02-12
Glad you got it solved.

---

