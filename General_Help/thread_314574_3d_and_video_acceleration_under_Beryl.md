---
title: "3d and video acceleration under Beryl"
date: 2006-12-07
forum: General Help
---

### Post by pgilmon on 2006-12-07
Hi all.

My PC is a centrino duo, 1 Gb RAM, nvidia GeforceGo 7400.

I have beryl 0.1.2 installed on Edgy. I followed the steps [here]("http://doc.gwos.org/index.php/BerylOnEdgy"). Everything works fine. The problem is that, although video and 3d acceleration works (glxgears and vlc), it is not as smooth as it is without beryl running. I can get it to run perfectly just by restarting X server and not starting beryl (I don't have to change anything in xorg.conf, just not start beryl).

How are things working for you? Does anyone have any idea whether this is a beryl/kernel/driver issue?

Currently I'm using lastest non-beta nvidia drivers (9631). As I have said, acceleration while I'm running beryl works, but with glxgears for instance, tha gears seems to stop for a moment from time to time, and the video is not played so smoothly.

I'm waiting for your feedback

---

### Post by strabes on 2006-12-07
Isn't that just because some of your video card's resources are being taken up by powering your desktop with aiglx? (I'm assuming you use aiglx since you have nvidia)

---

### Post by pgilmon on 2006-12-08
Yes, of course.

But, for instance, if I play a video in full-screen mode, it doesn't go smooth, whereas without beryl it does. While it is at full-screen it shouldn't be wasting resources in beryl, since I'm not spinning the cube or moving windows or anything. I guess that this is somthing that can be improved.

Beryl is still beta, I know. I just wanted to know people's opinion: whether this happens to everyone or it's just a problem with some cards, and if it's something that could actually be solved in the future...

---

### Post by UltraSonicSite on 2006-12-08
> **pgilmon said:**
> Yes, of course.

But, for instance, if I play a video in full-screen mode, it doesn't go smooth, whereas without beryl it does. While it is at full-screen it shouldn't be wasting resources in beryl, since I'm not spinning the cube or moving windows or anything. I guess that this is somthing that can be improved.

Beryl is still beta, I know. I just wanted to know people's opinion: whether this happens to everyone or it's just a problem with some cards, and if it's something that could actually be solved in the future...

Heh, spinning the cube. When I installed beryl I knew it was going to slow down other 3d programs/videos when it was on. That's why, like you, I made it to only start if I commanded it to. I think you can live with not having beryl on while playing a video. =P

---

