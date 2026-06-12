---
title: "Zesty 17.04, video and 2nd display problems"
date: 2017-04-17
forum: General Help
---

### Post by russkyca on 2017-04-17
I have no idea what to say or where to post this so I'll do the best I can.

I am just wondering if anyone knows what this is or has experienced it.

I have a 22" 1680x1050 monitor and 32" 720p TV - I use the TV to get a bigger picture.    I have the two display setup and I don't have any issues in 16.04 Ubuntu Gnome but I have another partition in which I installed 17.04 Gnome.   I installed the binary drivers, Nvidia 375 (I think).

Anyway, I am streaming a program and then I get artifacts and it freezes.... half the screen has a frozen image of what I was watching and the other half is a fragmented/artifacts display of the desktop.   It's weird.   I'm not sure how else to explain it.   I hope it makes some kind of sense of how I described it.   

How do I know what the culprit is?   Is there anything I can do to avoid this probem or fix it?   It's happened twice now.   I am not even sure I want to continue using 17.04 if this is going to happen often.   It has happened in the last two days and I installed 17.04 on the weekend (2-3 days ago).   

I don't know if it will happen with just one display.   It's just my experience with using a 2nd display.

Edit:   I forgot to mention!!!!    I cannot get rid of the fragmented/artifact screen.... I cannot close it (it's in a browser/window).... the way I see it, it's like the screen 'isn't refreshing.'   It's crashed....frozen....but, it's 'stuck.'   If I knew the process, could I 'kill it?'   Is there a process running that keeps the screen 'garbled' like that or is there nothing I can do?   

If I could 're-try' and run the stream again or go back to where it was, that would be one thing/option but I can't even refresh the screen...or get rid of it.   

Edit:  Is it Mutter / Gnome Shell crashing or something else????  :-(

---

### Post by sp40140 on 2017-04-18
First thing I would suggest to try is to use open source drivers and disable the Nvidia prop ones. And see if you can re-produce the problem.
The reason I suggest is that when I upgraded one of my computers from 16.10 to 17.04, I got into the login loop, where I would put password in and in a few seconds I would get kicked right back to the log-in screen. I booted with older kernel and it worked fine. So, I disabled the Nvidia prod drivers and booted with newer 4.10 kernel and everything is fine now. So, it just might be that the Nvidia drivers need some work for 4.10 kernel.

---

### Post by russkyca on 2017-04-20
> **sp40140 said:**
> First thing I would suggest to try is to use open source drivers and disable the Nvidia prop ones. And see if you can re-produce the problem.
The reason I suggest is that when I upgraded one of my computers from 16.10 to 17.04, I got into the login loop, where I would put password in and in a few seconds I would get kicked right back to the log-in screen. I booted with older kernel and it worked fine. So, I disabled the Nvidia prod drivers and booted with newer 4.10 kernel and everything is fine now. So, it just might be that the Nvidia drivers need some work for 4.10 kernel.
Just tried that.   It happened again.   Another crash - Chrome crashes - half the screen 'disappears' and the other side is 'pixelated/fragmented.'   I can't get rid of it either and anything I move or open up 'there' - obscured by the pixelated screen parts.  

I'm really disappointed in 17.04.   It seems like a failure and maybe it was released way too early.   I've never had such problems after a recent release.   I had other crashes too but I don't know how to save the error messages.   

There's no message when I get a crash of this kind, though.   

I don't know how to trouble shoot it but there was also another issue.   I was making a note in LibreOffice and when I tried to save, it the Office window went grey (as if greyed out) and I could only move the mouse.   I restarted the computer in disgust and booted up 16.04.    Like I said, Ubuntu 17.04 is a buggy failure!   If mods don't want people commenting on it, that just means there is something to hide.

---

### Post by russkyca on 2017-04-20
Would there be any difference with a different DE?   I don't know if it's the more recent kernel or what.   I can't find any threads similar to this problem.   What I am doing is SOOOOO common.... running a video stream... I should not have any crashes...  and when it does crash, it ABSOLUTELY should not crash with the browser 'still there' in a fragmented shape.   The process is dead.   I ran the top command and it's not running any more but the fragmented browser remnants are still there!   That's messed up!

---

### Post by sp40140 on 2017-04-20
It seems to me that your issues are not limited to display. So, I think we need more information.
Did you do in place upgrade to 17.04 or did you wipe older ubuntu and installed 17.04?
Also, with 17.04 Ubuntu includes beta version of mir DE (along with Wayland and regular gnome). Which one are you using? You can find this out at the log-in screen. 
You should use regular gnome (not mir or wayland).
Everybody's experiences differ on the OS. I moved all of my computers to 17.04 and didn't have any issues. Not to say that you don't have valid issues. We are here to help each other out. :)

---

### Post by russkyca on 2017-04-21
> **sp40140 said:**
> It seems to me that your issues are not limited to display. So, I think we need more information.
Did you do in place upgrade to 17.04 or did you wipe older ubuntu and installed 17.04?
Also, with 17.04 Ubuntu includes beta version of mir DE (along with Wayland and regular gnome). Which one are you using? You can find this out at the log-in screen. 
You should use regular gnome (not mir or wayland).
Everybody's experiences differ on the OS. I moved all of my computers to 17.04 and didn't have any issues. Not to say that you don't have valid issues. We are here to help each other out. :)I am pretty sure I mentioned in the beginning, it was a clean install.   I formatted the partition and installed as normal.   Where can you log out?   

This is the current information:
   Kernel 4.10.0-19-generic
  Nvidia driver ver:  375.39
  Gnome - GNOME Shell 3.24.0
  Ubuntu version:
 Distributor ID:    Ubuntu
 Description:    Ubuntu 17.04
 Release:    17.04
 Codename:    zesty


I'm also having trouble using Software Updates - one package won't update.   I'm really dissatisfied and disappointed with Zesty 17.04.   Maybe you just want to brag and laugh at my problems but why even mention that you have it working on all YOUR computers?   So, what?   Our computers/configurations are different... maybe you don't do anything on your computer or you don't do anything that gets the bugs to show up.   But, since I installed, I have had problems emerge fairly early and suddenly.   

Go check the forums for how many people have problems with 17.04.   I bet it will be a lot.   Tell them that your computers all work with 17.04.   I'm sure they'll be very impressed.

---

### Post by sp40140 on 2017-04-21
Can you please provide the screen shot of your log-in screen?
Also, have you tried to fix the broken packages? sudo apt-get update and sudo apt-get upgrade and sudo apt --fix-broken install commands?
I am not trying to brag. I was just trying to show that there are success and there are failures. It happens. I am trying to help. And learn things along the way.
If you find my comments lacking, let me know and I will stop here.

---

### Post by russkyca on 2017-04-21
> **sp40140 said:**
> Can you please provide the screen shot of your log-in screen?
Also, have you tried to fix the broken packages? sudo apt-get update and sudo apt-get upgrade and sudo apt --fix-broken install commands?
I am not trying to brag. I was just trying to show that there are success and there are failures. It happens. I am trying to help. And learn things along the way.
If you find my comments lacking, let me know and I will stop here.No, I appreciate you trying to help.... in fact, you're the only one so far.   But, I have read the similar 'it's working for me' so many times... I don't think people should say it unless they explain how it's working and how it's relevant to the person who is having a problem.   If you said, I have 17.04 working and I did the 'same thing as you' or I tried the same task....well, that would be something!   :)

Anyway... I hope you know what I mean and also, I am just frustrated.   Mostly cuz I don't understand what the problem is or what is actually happening when it fails.   Or what the culprit or culprits are.... video drivers, kernel, something else, etc

I ran 'sudo apt-get update' and there was no output that looked problematic.   Just the normal update output pattern.   I didn't try the others yet.  I have Gnome, Gnome Classic and Wayland as choices...

---

### Post by russkyca on 2017-04-21
Another problem in additional to tons of other problems...Display settings won't show up when I click it.   Also, 'Sorry, Ubuntu 17.04 has experienced an internal error...
Executable Path:   /usr/bin/gnome-control-center

Running out of patience with this.

---

### Post by russkyca on 2017-04-21
Settings won't show up at all.   I click it and nothing happens....Then, eventually, the same error message.   I guess Ubuntu and Gnome should be working together to fix the countless bugs and instead of releasing garbage and wasting people's time.

---

### Post by QIII on 2017-04-21
> **russkyca said:**
> Settings won't show up at all.   I click it and nothing happens....Then, eventually, the same error message.   I guess Ubuntu and Gnome should be working together to fix the countless bugs and instead of releasing garbage and wasting people's time.

I would suggest very highly that you drop the attitude.  There are many, many people for whom it is working fine.  Do not project your experience on the entire community.  Your sample size of one is not representative.

> **russkyca said:**
> If mods don't want people commenting on it, that just means there is something to hide.

What the "mods" don't want is a non-constructive, bilious attitude.  If you want to discuss *your* problems with 17.04, do so.  But check your poor behavior at the door.  ***THAT*** is the sort of thing that causes posts to be removed from public view.

---

### Post by sp40140 on 2017-04-21
My gut feeling on this is either you are running one of the beta DMs (mir or wayland) or you system wasn't installed properly. To confirm, you can let us know which gnome you are logging into. You should be using gnome classic.
If you are using gnome classic, then you should try out the remaining two commands from previous post. And if that doesn't work, then I think it would be easier to run installer and fix the os. 
Others with better knowledge can try to help you fix in different way.
Believe me, I am not the only one on this forums. Others are following this thread and will jump in when they think they have something to contribute.

---

### Post by russkyca on 2017-04-22
> **sp40140 said:**
> My gut feeling on this is either you are running one of the beta DMs (mir or wayland) or you system wasn't installed properly. To confirm, you can let us know which gnome you are logging into. You should be using gnome classic.
If you are using gnome classic, then you should try out the remaining two commands from previous post. And if that doesn't work, then I think it would be easier to run installer and fix the os. 
Others with better knowledge can try to help you fix in different way.
Believe me, I am not the only one on this forums. Others are following this thread and will jump in when they think they have something to contribute.I wanted to reply to you to confirm that I am using Gnome Classic.   

I think the problem isn't happening right now and I have tried to reproduce it.   I am not saying it's solved because I just noticed it not happening suddenly.   I didn't do anything or remember doing anything.   I'll re-post if it happens again.   If you think anyone is following the thread, I would like to state if the problem persists (just in case it happens to anyone else).  

This is the scenario in a nutshell:
Ubuntu Gnome 17.04 + using Chrome (usually happens in full screen) video streaming - so Chrome browser is full screen - and then video itself is made full screen.... soon after, the screen fragments and freezes....and is 'stuck there.'   Even the sound keeps going.... usually the fragmented part takes up half the screen and I can't get rid of it.   There are remnants of some pixelation.   If I drag some other window there, it only moves under the fragmented part of the screen.   I can't figure out how to 'refresh the screen' so I can get rid of it.   Therefore, the 2nd monitor (in my case, my 32" TV) is not usable so my option so far is to reboot the computer.   If I run top or look at what's running, Chrome is not running (I can close or kill that process) but the screen is still showing that 'crash.'

---

