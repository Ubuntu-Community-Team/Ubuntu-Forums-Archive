---
title: "Problems with TV monitor resolution"
date: 2017-03-20
forum: General Help
---

### Post by pam197 on 2017-03-20
I have recently installed Ubuntu 16.04 onto an old Dell Optiplex and am trying to use a new Logik Full HD TV as a monitor. When the TV is set to 16:9 and the resolution on the PC is set to 1920 x 1080 the screen has horizontal bands part of which are black and part of which show some of what I would expect on the screen. I have to change the TV to 4:3 display to be able to see enough of what is on screen to do anything. Changing the Screen display resolution to 1280 x 768 gives me a workable display with the TV set on 16:9, but when I logout or shutdown, the resolution obviously goes back to 1920 by 1080 and I have to change the TV back to 4:3 to log in again. Is there any way I can set the resolution to 1280 x 768 so that it remains even when I logout?

---

### Post by mörgæs on 2017-03-21
Hi, welcome to the fora.

Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. It will give people a better foundation for helping you.

---

### Post by pam197 on 2017-03-21
I think the result was too long so I have pasted it here [https://paste.ubuntu.com/24224412/](https://paste.ubuntu.com/24224412/)

---

### Post by mörgæs on 2017-03-22
Yes, it works fine like this.

I don't have experience myself with connecting to a TV but people who have might need the output for troubleshooting.

---

### Post by sp40140 on 2017-03-22
To answer your question: "Is there any way I can set the resolution to 1280 x 768 so that it remains even when I logout?"
Have you tried going to System Settings -> Displays -> change resolution to what you want?

---

### Post by pam197 on 2017-03-23
Yes, I changed the resolution using System Settings -> Displays. Is there another way to change the resolution? When I logout, I am guessing it goes back either to some default which I don't know how to change or possibly to the resolution it is getting from the monitor. When I login again, it has retained my setting of 1280 x 768. I just have a problem with how the screen displays when I logout or when I first turn on the PC.

---

### Post by garnget on 2017-03-24
so i found a fix for this on my tv.(it's a tcl ) not sure if it will work for you but it cant hurt to give it a go right, so go to the main menu on your tv. then to picture options and to advanced  and if you have a setting for hdmi mode switch it to graphic instead of video. this was the fix for the problem for me  hope it works for you too

---

