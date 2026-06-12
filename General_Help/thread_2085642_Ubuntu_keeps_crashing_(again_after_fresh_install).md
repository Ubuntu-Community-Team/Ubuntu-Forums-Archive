---
title: "Ubuntu keeps crashing (again after fresh install)"
date: 2012-11-18
forum: General Help
---

### Post by HandleWithCare on 2012-11-18
Hi all,

My ubuntu box keeps crashing for (to me) unknown reasons. This happend with 12.04 and the problem remains after a fresh 12.10 install. It is very unclear what happens. As soon as the machine start random applications fail and I'm shown a window stating Ubuntu had an error and the application must be closed. It is a different application every time. Then at some moment, sometimes within a minute, sometimes after two days the machine just stops. Sometimes I just get a black screen, other times I get screens as in the photos I attached (different every time) and at other times there is no output to my screen at all anymore.

I have no idea what information would be needed to tackle this problem but the output of lshw can be found here: [LIST OF HARDWARE]("http://seedoubleyou.nl/hw.html") .

Normally I would take a look in the logs but another unfortunate part of this problem is that >14GB of system log is created, which is, a lot.

I have done a memcheck and diskcheck. No errors were found.

Any hint on how to fix this problem is very welcome.

---

### Post by mörgæs on 2012-11-19
Please give a complete hardware description. 

Have you tried the memory test in a live boot?

---

### Post by HandleWithCare on 2012-11-19
There is a link in the topic start to the complete hardware list, I made the link more prominent. I also updated the post with the fact that I did disk en memory checks and that no error were found during.

---

### Post by mörgæs on 2012-11-20
It seems you have both Nvidia and Radeon graphics cards. Have you tried removing one of them?

---

### Post by HandleWithCare on 2012-11-20
Actually there is only one graphics card (ati). There are no onboard graphics either.

---

### Post by QIII on 2012-11-20
Does this happen in a Live CD session with Ubuntu?

Try a live session with another distro.  Does it happen then?

Are you sure your install media is clean?

As large as they are, your logs are probably a very valuable resource for troubleshooting this.

---

### Post by HandleWithCare on 2012-11-20
I have not seen this problem in a live session. However, as I mentioned the problem does not occur after a fixed time period. Sometimes it runs for two days without crashes

---

### Post by HandleWithCare on 2012-11-20
I have not seen this problem in a live session. However, as I mentioned this problem does not occur after a fixes time period. Sometimes it runs for two days without crashes

---

### Post by Cope57 on 2012-11-20
My guess would be a hardware failure.  Could be the commonly overlooked power supply or simply some connections have come loose.

---

### Post by HandleWithCare on 2012-11-20
Yes that was my guess as well. All connections seem fine. I have replaced the power supply to no avail.

---

### Post by Cope57 on 2012-11-20
Any response with the bug report? [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

What errors do you have in your logs?

---

