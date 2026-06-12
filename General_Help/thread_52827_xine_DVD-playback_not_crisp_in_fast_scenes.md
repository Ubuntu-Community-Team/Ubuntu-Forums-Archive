---
title: "xine DVD-playback not crisp in fast scenes"
date: 2005-07-29
forum: General Help
---

### Post by Juggernaut on 2005-07-29
Hello,

I've got a problem with xine.

Whenever I'm watching a DVD in fullscreen, during (more or less) fast scenes some lines of the screen are omitted and the image
isn't quite crisp. The 20th Century Fox logo flying in would be an example. 
I'll see if I can upload a screen-shot later.

In general, DVD playback is smooth and I have DMA enabled. 

I thought it might have something to do with interlace, but pressing "i" wouldn't help.
However, I can't change the "interlacing mode" (?) in the video settings, as some homepage suggested. 

I think I already had this problem with xine and another distribution and starting xine with some parameter did the trick (I guess)

I installed xine out of synaptic, and I prefer it to mplayer because it supports menus (mplayer doesn't AFAIK).


Thanks for any suggestions!

---

### Post by super on 2005-07-29
yeah that does sound like the interlace settings.

to change it in the xine preferences you need to enable "master of the known universe" mode and then turn on the deinterlacing.

otherwise edit the value in the xine config file in $HOME/.xine

or use vlc.

---

### Post by Juggernaut on 2005-08-01
Thanks for your reply!

I still don't quite get it.

I chose "Master of the Universe" in the preferences, but still there is no way to change interlace settings in the video tab.

I am not sure if xv is even installed correctly on my system. Xine claims to use it, but I can't get it to work with mplayer.

In Gnome's system settings, I can test if multimedia settings are ok, but for some reason I can't test my output settings.

I'm using a Radeon 9200 with ATI drivers installed as described in the HowTo's. 3D support seems to be enabled (all those fancy screensavers run smoothly and didn't before)

---

### Post by super on 2005-08-01
have you selected "enable deinterlacing by default" on the "gui" tab? that should be turned on as well.

then restart xine and it should say "deinterlacing enabled" in the top left of the video window when it starts.

---

