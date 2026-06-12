---
title: "streaming live video to skype video"
date: 2015-12-07
forum: General Help
---

### Post by Robbyx on 2015-12-07
Can I stream my webcam output being picked up by VLC on /dev/video0 to stream it to /dev/video1? I want to use VLC as the cam controller. I am hoping that if I look at the video source options in skype it will show both video0 and video1.

---

### Post by Ricardo_Velasco on 2015-12-07
Greeting:

To understand a little your question ? Could you explain me more detail please ?.

Tell me your webcam ?.

---

### Post by Robbyx on 2015-12-08
Thank you for coming to my rescue. 

Ubuntu does not seem to have an app that enables the adjustment of all the benefits available in the logitech C920 cam. The nearest I have found is VLC's v412 controls. It does everything very well,  except for allowing the video output to be changed. 

VLC  does not allow skype to access the webcam at the same time as it is being actively controlled by VLC. It therefore seems desireable to have the video cam output to go first to VLC via /dev/video0  and then to stream the video  from VLC to skype via  /dev/video1, but I do not know how to do it.

R

---

### Post by Ricardo_Velasco on 2015-12-08
Greetings:

Investigate and found a possible solution to your problem , you can create a duplicate device dev / video0 dev / video 1

Forgive me for not giving the steps personally . I share the link AskUbuntu page:

> [http://askubuntu.com/questions/416380/how-to-create-a-duplicate-of-dev-video0](http://askubuntu.com/questions/416380/how-to-create-a-duplicate-of-dev-video0)

---

### Post by Robbyx on 2015-12-08
Thank you for finding that advice. It is a bit hard to follow some of it, but I will try.

---

### Post by Ricardo_Velasco on 2015-12-08
Cheers:

I investigate more and I also found this site, I share :

> 
[https://www.timdejong.nl/blog/use-webcam-two-applications-under-linux-simultaneously-using-v4l2loopback](https://www.timdejong.nl/blog/use-webcam-two-applications-under-linux-simultaneously-using-v4l2loopback)

---

### Post by Robbyx on 2015-12-09
Thank you for finding that extra source.

---

### Post by Robbyx on 2015-12-09
All the suggestions do not seem to work without in depth knowledge. I have tried them all and every one has some problem that stops it from working. It is beyond my knowledge to get any one to work,  and so  I hope a solution that works out of the box will soon  become available.

---

