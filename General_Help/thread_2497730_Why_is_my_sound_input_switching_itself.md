---
title: "Why is my sound input switching itself?"
date: 2024-05-15
forum: General Help
---

### Post by dorasmith24 on 2024-05-15
Why would my mic switch ITSELF in settings in mid use?   It suddenly changed itself from my USB headset to my webcam and neither was actually getting my voice, eg, couldn't record and play it back.   

I was working at my work from home CSR job.   I didn't reboot my computer or put it to sleep and wake it up, or walk away from it and wake it up.

Somehow in switching back and forth it suddenly started working again.

Webcam doesn't mute and headset wasn't muted.

I'm using Ubuntu 20.04.  On my desktop.

---

### Post by TheFu on 2024-05-16
PulseAudio will switch to a new input whenever it is plugged in.  This is the default policy.  I think one of your connections is flakey.  The easy answer is to only have 1 connection active at a time.  If the problem is with an internal microphone, then you can use **pavucontrol** to disable it in the far-right tab.

---

### Post by dorasmith24 on 2024-05-16
Thanks.  I'll try unplugging the webcam and see if that fixes it.

---

### Post by TheFu on 2024-05-16
> **dorasmith24 said:**
> Thanks.  I'll try unplugging the webcam and see if that fixes it.

It is the plugging in, not the unplugging that matters.  So, you may need to unplug the webcam, then unplug the USB mic, wait 10 seconds, plug in the USB mic, then start your application.  Many applications don't dynamically see audio equipment changes.  Some do, but many do not.

---

### Post by dorasmith24 on 2024-05-16
What is pavucontrol?   Are you simply talking about settings?   I don't actually see a way in settings to disable it, though it seems like that should be there.   Is Pavucontrol something I have to install?   I can't find it in my applications.

---

### Post by TheFu on 2024-05-16
> **dorasmith24 said:**
> What is pavucontrol?   Are you simply talking about settings?   I don't actually see a way in settings to disable it, though it seems like that should be there.   Is Pavucontrol something I have to install?   I can't find it in my applications.

If you unplugging/replugging works, then you don't need it.

pavucontrol is the Pulse Audio Controller from the pulse team.  Ubuntu doesn't ship with it - they provide a stupid version - that must be too dumb for your needs.  You may need to install it.  Open a terminal and see if that command works or not.  Often if it isn't installed, the output there will tell you the exact command needed to install it.

BTW, google would have answered all this.

---

### Post by dorasmith24 on 2024-05-16
When I typed pavucontrol in applications it brought up Pulse audio, but the settings are hardly intuitive.  Can someone please review it and tell me if I need to make changes to make it stop screwing with my choice of input mic setting, whether that's my webcam or my usb headset.  I especially need it to work properly when working from home doing call center.

I THINK I attached two screenshots, but the method to do that is about as intuitive as pavucontrol.

---

### Post by TheFu on 2024-05-16
In the far right tab, set the microphone you don't want used to  "off".  That's it.  When you want to use it again, run the program again and turn it on and turn off the other microphone.

Or you can use the Input Devices tab and use the "disable" button (the little speaker" for each input.  Best to leave the monitor  enable, if you do any screen recording.  Only have 1 input device enabled at a time.

---

