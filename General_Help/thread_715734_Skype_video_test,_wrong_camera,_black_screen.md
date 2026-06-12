---
title: "Skype video test, wrong camera, black screen???"
date: 2008-03-05
forum: General Help
---

### Post by cisforcojo on 2008-03-05
I'm using a very very cheap USB camera that I bought in China.
Here's my lsusb:
```
Bus 004 Device 003: ID 0c45:602c Microdia Clas Ohlson TWC-30XOP WebCam

```

I've gotten it working in camorama using the gspca driver (built from the gspca-source package) and I've blacklisted the default (but not working) sn9c102 driver (there's conflicts). 

My problem is, when I go to the video test in Skype, it lists my camera as a sn9c101??? And when I test it it's just a black screen. Any ideas???

---

### Post by wieman01 on 2008-03-05
Mine does not work either, when I do a test video. You need to call someone to really find out if it works. Mine does, although the test video fails. Greetings from Qingdao/Shandong. :-)

---

### Post by cisforcojo on 2008-03-05
Great! I'll just try a call then. I was in Qingdao visiting a little over a year ago. Great city! I loved Lu Xun Park and the pine trees on the beaches.

---

### Post by wieman01 on 2008-03-05
I love Qingdao as well. Never been to Nanjing though, but I know a little about its more recent history. Pretty said, so I look forward to seeing it one day to learn more about it.

If the call fails, you know where to find us.

---

### Post by cisforcojo on 2008-03-08
Are you using the gspca driver? How is the quality from your webcam? Mine is 'working' but it's really really blurry. (This is just in camorama and vlc. Haven't tried a call yet.)

---

### Post by vivalant on 2008-03-08
Have you had a look at the SN9CXXX binary-only driver? [http://www.linux-projects.org](http://www.linux-projects.org)

---

### Post by cisforcojo on 2008-03-15
Yeah I've seen it. The driver is about half the price of the webcam though (ie not worth it). The webcam is really just something cheap I picked up. I'd be better off just getting a better supported webcam. It's interesting for me to try and get this one working. I'm learning a lot about drivers and modules and everything. Thanks for the idea though!

---

