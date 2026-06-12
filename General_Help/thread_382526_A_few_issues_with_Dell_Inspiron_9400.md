---
title: "A few issues with Dell Inspiron 9400"
date: 2007-03-12
forum: General Help
---

### Post by mrwooster on 2007-03-12
Hi,

I have been running Dapper on my Dell inspiron 9400 for a couple pf months now and almost everything is working fine, however there are just a couple of things which I am having trouble with and some advice would be great.

1) - When I use the sleep button on my computer it works fine the first time, however, when I try to use sleep again it goes to a blank screen, flashes up and error in white text for a split second (too fast to read) and freezes on a black screen until I re-boot. Once re-booted, sleep will agian work once only.

2) - About 1 in 5 times, when I shut down the computer (I log out and then shut down), when I click log out, the computer goes to a black screen and freezes (no error message) and I have to turn it off manually.

3) - In windows, I have a battery life of about 2h30m whereas in Unbuntu its only 1h30m, is there any way to increase this?


These are minor issues, but it would be nice to be able to find some solutions.

Thanks

Guy

---

### Post by mrwooster on 2007-03-12
Bump: Any ideas?

---

### Post by grogger13 on 2007-04-03
i have the same problem with battery life.  to bad nobody will help us.

---

### Post by Cloudy on 2007-04-03
I'm having similar problems with battery life as well.

---

### Post by vav on 2007-04-05
+1 on low battery life... this time with an inspiron 9300 - through dapper, edgy and now feisty.

Your first 2 problems mrwooster, might be related to the graphics driver. If you have an ati card, the open source radeon driver is the best. If you have this configuration, try enabling the clock scaling for the graphics card - might improve battery life (didnt for me [https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/97627](https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/97627))

---

