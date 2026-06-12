---
title: "Completely lost"
date: 2007-05-28
forum: General Help
---

### Post by heaver on 2007-05-28
hey guys...i dont know if this is the right section or whatever but....i installed ubuntu today on my laptop but my usb mouse never worked, it wouldnt be a problem if the touchpad wass working...but it isnt ^^
i dont know what to do...i cant open the applications or anything...im only stuck i tried everything on the keyboard to try to open the applications but it didnt work ^^

if anybody could help me...id really appreciate

---

### Post by heaver on 2007-05-28
amazing how helpful ppl can be oO

---

### Post by mac173 on 2007-05-28
LOL, give it time. I don't know the answer myself, or I would tell you. 

Good luck with your laptop though.

---

### Post by heaver on 2007-05-28
time?? lol...ivw been breaking my head all day trying to solve this...the internet is wireless and is not working in my laptop either

---

### Post by heaver on 2007-05-28
just found that the usb ports are not working either...and i already tried reinstalling ubuntu

---

### Post by Dylnuge on 2007-05-28
Time as in since you posted, not since you started having the problem. Its only been an hour since you posted, no one could help you before that.

If you can use your keyboard, you are all set to do what I want you to do right now:

1. Boot your computer
2. Choose Recovery in the Boot Menu (second option)
3. Once logged in, type this command:
```
nano /etc/X11/xorg.conf
```
4. Scroll down until you find a section that begins Input Device-Generic Mouse. There may be an entry for your touchpad, ignore it for now. Copy down wahat you see (by hand) and post it here.

If you have a USB jump drive I can walk you through transfering files that you will need to post here to your jump drive.

Sounds like you have a lot of problems. Mind posting what computer you have here, IE, some basic information about it. Posting the results of a lspci here would be very helpful.

---

### Post by Dylnuge on 2007-05-28
Okay, I am going to go ahead and make some assumptions and priorities:

1. Your mouse and USB problems are seperate. Your USB mouse and Touchpad problems are much more likely to be related.

2. You probably can't get wireless working without your mouse, regardless of whether or not you need an access key. Ubuntu won't connect by default.

3. You are going to need to do a lot of console work. A lot. Don't be scared off by the console. If this were a windows problem, you would need to take your PC into a technician. The console is rarely, if ever, needed, but in advanced cases like this, it is eaiser to check deep system config files then blindly troubleshoot.

Also note that I am watching this thread. That means that I may not always be online, but I will always get back to this thread and try and post. It may be a few days before this issue can be resolved.

So, most important things I need right now:

1. Do you have a Jump Drive
2. Type lspci at the console and post the results.
3. Open the Xorg.conf file and post the mouse section.

Note: Info on how to do the last two is above.

---

### Post by Dylnuge on 2007-05-29
After posting about how upset you are when no one answered, I am suprised to not get a response when someone does.

---

