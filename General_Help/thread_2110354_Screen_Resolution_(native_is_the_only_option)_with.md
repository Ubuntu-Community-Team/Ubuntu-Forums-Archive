---
title: "Screen Resolution (native is the only option) with nvidia drivers"
date: 2013-01-30
forum: General Help
---

### Post by cruz12141214 on 2013-01-30
hello 

I have been using ubuntu for a while now, and it works fine, but i have an issue that im sure is common, i just hope it is some thing that can be fixed and is not an issue with NVIDIA

ok I have the Asus g74sx -bbk7:  with the gtx 560m 2gb VRAM

the issue is Im currently using the nvida drivers (nvidia-current) i think its version 310.19 

but when i try to change the resolution on my screen i only have one option, the native one (1600x 900)

external monitors work fine though.... i can change the resolution on those,

but not my built in monitor

is there a fix for this? or is it some thing that Nvidia needs to fix?


just in case here is my xorg file


oh and thanks in advance

---

### Post by sudodus on 2013-01-30
- Why do you want to change from the native resolution? This may give us ideas how to solve your problem.

- What is the output of the following command
```
xrandr
```

- Which version of Ubuntu are you running (12.04 LTS or another one)? Have you tried another version?

---

### Post by cruz12141214 on 2013-01-30
well some times i have to reduce the resolution depending on what i connect to



roberto@roberto-G74Sx:~$ xrandr
Screen 0: minimum 8 x 8, current 1600 x 900, maximum 16384 x 16384
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 connected 1600x900+0+0 (normal left inverted right x axis y axis) 382mm x 214mm
   1600x900       60.0*+
HDMI-0 disconnected (normal left inverted right x axis y axis)
roberto@roberto-G74Sx:~$

---

### Post by sudodus on 2013-01-30
Try according to the following link

[[COLOR="Red"]http://www.arunviswanathan.com/node/53[/COLOR]]("http://www.arunviswanathan.com/node/53")

> For making it persistent, one option is to add those lines to your /etc/profile file.

---

### Post by cruz12141214 on 2013-01-30
i tried it but it would not work


thanks for the help though

it might just be an nvidia thing


do you know the resolution switcher indicator?

well i just tried with that and i can switch my resolutions between (1600x900) , (1280x720), (1024x 768), (800x600), (640x480)

choosing the "configure display settings" option of that indicator gives me this:

Failed to execute child process "/usr/bin/gnome-display-properties" (no such file or directory)

but then agin i am using the nvidia drivers so thats probably why

---

### Post by sudodus on 2013-01-31
> **cruz12141214 said:**
> 
well i just tried with that and i can switch my resolutions between (1600x900) , (1280x720), (1024x 768), (800x600), (640x480)

Yes, maybe (or probably) the problem is caused by the proprietary driver.

But it was not quite clear: Can you switch your resolutions between (1600x900) , (1280x720), (1024x 768), (800x600), (640x480)?

And in that case, it that satisfactory?

---

### Post by cruz12141214 on 2013-01-31
yes i can but only by using the resolution indicator, its just weird, I cant change the resolution using the nvidia manager or the display manager

---

### Post by sudodus on 2013-02-01
I'm glad you have a way of setting the screen resolution :-)

I have no idea why it is like this. Probably a later version of nvidia's driver will make things smoother.

---

### Post by cruz12141214 on 2013-02-01
yeah currently im using their latest one, i think its 310.58 or something like that

---

