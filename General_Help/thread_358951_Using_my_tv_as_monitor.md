---
title: "Using my tv as monitor"
date: 2007-02-11
forum: General Help
---

### Post by SirPaPa on 2007-02-11
Hi, I'd like to know if I can connect my tv to my computer using the s-video jack and how do I go about it. Thank, you very much.

---

### Post by g8m on 2007-02-11
Yes you can. Just plug the cable in between tv and computer and restart X. 
You must have installed the specific drivers for your videocard. 

In my case, my laptop has a sis videocard, I had to edit the /etc/xorg.conf
and replase the driver vesa with sis. 

For Ati/Nvidia it will be different, but there will be a lot of howto's around, just do a search.

---

### Post by reclusivemonkey on 2007-02-13
> **SirPaPa said:**
> Hi, I'd like to know if I can connect my tv to my computer using the s-video jack and how do I go about it. Thank, you very much.

I would assume (always a bad idea) that connecting your tv to the computer means you want to get the output from your tv to go into your computer. Or do you mean you want your computer's video output to appear on your TV?

If you are running edgy, then you should automatically get a picture just plugging the video out from your graphics card to your tv. However, tweaking xorg.conf to the correct values can get you much better results. I have a HTPC connected to a widescreen tv and although it magically displayed everything on the install, once I had MythTV up and running, editing the xorg.conf gave a much clearer picture.

---

### Post by SirPaPa on 2007-02-17
> **reclusivemonkey said:**
> I would assume (always a bad idea) that connecting your tv to the computer means you want to get the output from your tv to go into your computer. Or do you mean you want your computer's video output to appear on your TV?

If you are running edgy, then you should automatically get a picture just plugging the video out from your graphics card to your tv. However, tweaking xorg.conf to the correct values can get you much better results. I have a HTPC connected to a widescreen tv and although it magically displayed everything on the install, once I had MythTV up and running, editing the xorg.conf gave a much clearer picture.

What I meant was to use my tv as my computer monitor. I connected An s-video cable from my computer's graphic card to my tv but the graphics are crappy at best. I missing something just don't know what. Plz help. Thank,you all.:-k

---

### Post by fragos on 2007-02-17
The TV isn't capable of the higher resolutions available on most video cards.  I may be mistaken but believe you need to use 1024x768.

---

### Post by rsambuca on 2007-02-17
The best a TV can receive over S-Video is 480i.  Not good enough to use as a monitor for anything other than video playback.

---

### Post by SirPaPa on 2007-02-17
> **rsambuca said:**
> The best a TV can receive over S-Video is 480i.  Not good enough to use as a monitor for anything other than video playback.

So, does this mean I cannot use my tv as a monitor at all? What else is the purpose of video cards with S-video jack, just for other monitors? Please explain. 

P.S.  I went to Radio Shack a couple of days ago and the rep there said I needed a signal converter for this to work.

---

### Post by rsambuca on 2007-02-17
Yes, you can definitely use it as a monitor, but with a resolution of 640x480 only.  Most monitors that people use on their desktops are 1280x1024, or 1024x768.

At 640x480, it really isn't all that functional if you want to do work with spreadsheets or word processing.  If all you are doing is surfing the net, then you may get away with it.  You will have to play around with your default fonts to get them readable.

The S-Video jack is very handy if you want to use your PC as a PVR using a tuner card.

---

### Post by SirPaPa on 2007-02-17
> **rsambuca said:**
> Yes, you can definitely use it as a monitor, but with a resolution of 640x480 only.  Most monitors that people use on their desktops are 1280x1024, or 1024x768.

At 640x480, it really isn't all that functional if you want to do work with spreadsheets or word processing.  If all you are doing is surfing the net, then you may get away with it.  You will have to play around with your default fonts to get them readable.

The S-Video jack is very handy if you want to use your PC as a PVR using a tuner card.

Thank,you I was just hoping I could use my tv as my monitor. I guess the rep at Radio Shack was right, but that coverter costs $80.00. Well thank you for your time.

---

### Post by tenjin1 on 2007-12-09
I am using S-Video out on my NVidia graphics card to the TV and cannot go over 1024x768 resolution. My TV can handle up to 1366x768. I have edited my xorg.conf properly by adding the higer resolutions. 

So according to what some of the posters said I'm not going to be able to go over 1024x768 on S-Video? Seems like this is correct, since I have been fiddiling with xorg.conf and doing everything right. If anyone is able to get over a resolution of 1024x768 using S-Video out to their TV...then please let me know what you have done! :) thanks

(I will more than likely end up using a DVI-to-HDMI cable from my NVidia card to the TV or a VGA cable, since my TV has a VGA in)

---

