---
title: "Black Screen When Booting Using Wubi"
date: 2008-01-06
forum: General Help
---

### Post by 03myersd on 2008-01-06
I had ubuntu dual booting on my computer a long time ago, when the drive failed and i got a new one I never bothered putting ubuntu back on again. I decided to do it now though. I tried using Wubi to install it. Everything went fine. Then when I tried to boot into ubuntu there was just a black screen with white dots flashing about. I read the other threads and I got past this by pressing ctrl+alt+f1  (although I think it was luck). I played around with it for a few minutes before installing updates. 

Once I had done this it asked me to restart. I did so and I was back to the black screen. After a while the white dots stop.

I am sure it is a problem with my monitor. By leaving it to make sure the logon screen was up I typed in my username, pressed enter, typed my password, pressed enter and I assumed it would now be on the desktop. I pressed ctrl+alt+f1 again to get into the console. Then when I typed a few things and pressed backspace too much it beeped just like it had done when I could see it.

It seems resonable to assume that everything is loading fine it is just now displaying on the monitor? It is a Philips 190WV with a resolution of 1440x900.

There seems to have been problems like this before with widescreen monitors but none were using wubi.

Thanks in advance for any help i receive!!

---

### Post by ago on 2008-01-07
If you can get to a console run

sudo dpkg-reconfigure xserver-xorg

try to start with a vesa driver

---

### Post by 03myersd on 2008-01-07
What will come up on the screen so I know what to press? It's quite hard not seeing it... Lol.

---

