---
title: "Do you know how to get the MIDDLE button to PASTE like it did before?"
date: 2013-04-24
forum: General Help
---

### Post by fixitdude on 2013-04-24
I tried to find this setting, I know it's there somewhere.

If you don't know what I am talking about, I used to be able to hit the middle button (or click left and right buttons together) to PASTE from the second clipboard.

Yes, there used to be TWO clipboards, one you select from a menu as "copy" or "paste" and one where you select something by left clicking and dragging the mouse and selecting text from ANYTHING, then you can paste that with the middle click.

What happened in 12.04 that took it out? I use it all the time, if you never used it you should try it because it saves a lot of time!

Thanks for any help.

Kubuntu with 12.04 install and now using the "Trinity Desktop" from [http://www.trinitydesktop.org/](http://www.trinitydesktop.org/) it's great, check it out!

---

### Post by hkphooey on 2013-04-25
I think this is a function of the desktop, so perhaps installing trinity broke this for you?

---

### Post by fixitdude on 2013-04-25
> **hkphooey said:**
> I think this is a function of the desktop, so perhaps installing trinity broke this for you?Thanks for taking the time to reply.

Does it work for you? I'm not sure if they decided to take that feature out because it was confusing people. I hope not because it's a super time saver.

Same problem on the default KDE that came with the Kubuntu install which may be a clue.

Is there a low level mouse driver that sits below the desktop and has settings for this? How do I get to that?

---

### Post by Locus Kiesselbachi on 2013-04-25
I have always dreamed of multiple "clipboards".

---

### Post by pqwoerituytrueiwoq on 2013-04-25
works on my kubuntu 13.04 live usb
i use that feature all the time, i use xubuntu myself

---

### Post by fixitdude on 2013-04-25
Guess what I found!

"Author: Peter Hutterer <email address hidden>" ..... "Disable the feature by default instead. There's not a lot of two-button mice around anymore"

"Bryce Harrington" .... "2-button mice do not seem to be very common"

COMPLETELY STUPID ASSUMPTION! These guys win an award! And although I appreciate the developers and everything they do, this attitude of "everyone is like me and buys all new stuff every year" or "everyone has a super high speed connection and so I can make HUGE files and it doesn't matter" or "everyone has a perfect internet connection so you don't have to bother with download retries" is the big problem with Linux in general.

These guys need to learn to ASK THE COMMUNITY before making big changes like that !!!!!! Not everyone lives like you do!

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/710762](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/710762)

The fix is to edit /etc/X11/xorg.conf   <<< BUT THERE IS NONE IN 12.04 !!! It's just not there WHY ???

Another suggestion is to install:

sudo apt-get install gpointing-device-settings

Run it from a terminal and select "Middle Button Emulation".

THAT WORKS! I don't know what it does exactly but it works perfectly now and I didn't even have to log in again.

HOPE THIS HELPS SOMEONE !!

And developers: WHY ??????? Stop screwing things up !

---

### Post by Feathers McGraw on 2013-04-25
> **fixitdude said:**
> 
What happened in 12.04 that took it out? I use it all the time, if you never used it you should try it because it saves a lot of time!


I'm using Kubuntu 12.04 and it definitely works...in fact it's a bit of a pain sometimes, I keep accidentally pasting as I scroll up the page.

[This link](https://wiki.ubuntu.com/X/Config/Input#Example:_Disabling_middle-mouse_button_paste_on_a_scrollwheel_mouse) covers disabling the middle scroll wheel button, I use it when it's frustrating me. The same process should work in reverse to re-enable it!

Feathers

---

### Post by colin.p on 2013-04-25
Thanks, I never knew that existed. I just tried it in ubuntu 12.04 and it works. Cool, two clipboards. Not sure I'll use it much, but I'll try to remember it's there.

---

### Post by Theredbaron1834 on 2013-04-25
> **fixitdude said:**
> 
Yes, there used to be TWO clipboards, one you select from a menu as "copy" or "paste" and one where you select something by left clicking and dragging the mouse and selecting text from ANYTHING, then you can paste that with the middle click.


O crap. I knew there was a second, but I thought that was used when you selected everything, and then copied. I didn't know you just have to select. 

I know this isn't helping you, but I like it. Still works with openbox, so thanks. :)

---

