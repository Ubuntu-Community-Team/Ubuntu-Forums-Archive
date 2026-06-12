---
title: "How can I make Ubuntu detect my screens properly?"
date: 2015-03-10
forum: General Help
---

### Post by jackhe220 on 2015-03-10
I use a SHARP TV as my primary monitor set to 1920x1080 in Windows just fine. My second monitor is a 1280x1024 LCD. In Ubuntu, however, the max resolution my TV can be set to is 800x600, and the max res of my second monitor is 1024x768. This happens after I install the nvidia driver for my card. I've tried the xrandr mode add and all that jazz, but that just chucks up errors, and ultimately doesn't work. On first boot at the login screen, the resolutions were correct. The TV is connected via HDMI, the second monitor is connected via DVI-I, and the card is the GTX 970. Thanks!

---

### Post by pmi2 on 2015-03-11
What do you see in System Settings, Displays?  

Are your monitors recognized as anything that resembles what they are, or do they appear as "Unknown Display", or some other kind of Monitor?

---

### Post by jackhe220 on 2015-03-12
Hi, thanks for your response.
They were both appearing as Unknown monitors, but I've managed to fix the issue for now. I dumped my EDID files from both my monitors in Windows, and just set my Xorg to use them. After doing that, the resolutions, names, etc are all correct!

---

### Post by pmi2 on 2015-03-13
Sounds like a good alternative.  You could post some directions for other people with less common monitor combinations.

---

