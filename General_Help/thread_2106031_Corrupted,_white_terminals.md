---
title: "Corrupted, white terminals"
date: 2013-01-17
forum: General Help
---

### Post by Arith on 2013-01-17
I apologize if this has been addressed. I've searched here and in google to no avail. Perhaps my google-fu is failing me, who knows.

Anyway, my problem isn't really an important one, just an annoyance. It seems that in (for lack of a better term) "pure" terminals; ie. if I hit crtl-alt-f1, I'm at a new session, or during a bootup/shutdown. At those times, I get a screen full of white, with some characters showing (heavily corrupted). However, if I go into a terminal within gui it's perfectly fine.

Please forgive me for I am extremely rusty in Linux in general, but have used in the past very sporadically. In other words, experienced but so rusty I might as well be noob. That being said, I'll give as much info as I can think of that can be relative:

System Hardware:
AMD Athlon II x4 (645)
4gb RAM
ATI HD6850 (Sapphire, toxic) in a triple monitor setup

Software:
Ubuntu x64 12.04, fully updated as of about an hour ago (dedicated partition)
Using restricted ati drivers (fully up to date)
* I've seen hints that GL might have issues, but compiz seems to behaving, as well as most native games. I don't think it's related, alas.

All I can think of is xorg configs. Then I can remember being reduced to a blubbering mass after spending entire weeks diagnosing xorg and ati hardware. So, I'm prevailing on those who hopefully know better. Anyone have any tips on possibly solving this annoyance?

---

### Post by Tralce on 2013-01-18
Have you tried logging in to these pure terminals anyway? just type your username and password like you normally would. See if typing "reset" and enter helps. 

Also, can we get a picture of this? I know screenshots are out, here, so a camera?

---

### Post by Arith on 2013-01-21
So, here's a bit of fun. I've continued to have the issue up until about 20 minutes ago.

I had a different issue with VLC not playing audio. During my troubleshooting, I did "touch /forcefsck" (near as I can recall it) Rebooted, it did it's thing. After another 30 minutes of troubleshooting (consisting of switching VLC output a few times, and not much more) I finally fixed the audio thing. Cool, now to move on to getting a screenshot for you nice people.

I can't reproduce it now.

You'd think the disk check did SOMETHING to fix the issue.. but that's not the first time I've run fsck. So, I'm at a loss as to what exactly happened here. If the issue comes back, I'll pick up where we left off. For now, I guess we'll just have to ponder on the possibilities.

Thanks for the reply at least :)

---

### Post by Arith on 2013-01-23
Seems it's come back after a cold boot. In the good news department, I got a [_screenshot_]("http://i138.photobucket.com/albums/q257/Serojin/20130121_213557_zps8926aa1c.jpg")

I tried logging in as myself and feeding it "reset" as Tralce suggested, to no avail. I have no idea what the output was, but near as I can tell it just gave another prompt on the very next line.

Any thoughts?

---

### Post by nwalkey on 2013-01-23
I've seen this with computers in our lab and it seemed to be a frequency issue with the monitor or something similar. We just switched out the monitor for a different one and the problem is gone. But if it works and you don't need tty access then it likely isn't going to cause you any trouble.

---

### Post by Tralce on 2013-01-23
I am lost, to be honest, but it may be helpful to point out that "reset" definitely did not do what I was expecting it to, which is to clear and reinitialize the terminal. Instead it just printed a new line with a new prompt, as if you'd just hit enter. Weird.

---

### Post by Arith on 2013-01-23
Forgive me, I wasn't remembering things correctly. I did the reset about a day or so ago. It does clear it (I just tried) all it does is make those vertical lines in the bottom go all the way to the top of the screen.

nwalkey raises an interesting point. I have a TV in the mix of my 3 monitors via hdmi.  ..  which then immediately points me back to xorg configs. I don't even know if xorg is relevant these days. Unfortunately I haven't even tried to look in my machine for the configs for lack of time really.

The odd thing is that running fsck fixed it until I powered down. Well, I guess I can poke around my system for a few minutes tonight and see what I can dig up.

---

### Post by alexr1090 on 2013-01-23
Hello. I've got a hunch it could be the ati drivers. Did you try running your terminal while plugged into onboard and seeing if that could be the issue?

---

### Post by Arith on 2013-01-23
Wouldn't surprise me in the least that it was ATI drivers. Unfortunately I don't have an onboard vga on this rig. 

My gut is so far going with the refresh rate theory. I'm looking around the settings for any hints - found xorg configs. Once I came out of my horrific flashback episode and 3 stitches later I decided that if it requires me to do severe changes to xorg.conf I'm just not going to bother with it. 

We shall see..

---

### Post by alexr1090 on 2013-01-23
hopefully you find a solution to this. I had same problem after installing an nvidia card (with nvidia's proprietary drivers). Sometimes it would work sometimes it wouldn't. I got rid of nvidia's drivers and used nouveau. Since then it appears to be alright booting into the pure terminal. I still get weird white lines when booting up though.

---

### Post by Arith on 2013-02-06
Alright, so a little progress. I finally got around to addressing this. It seems that it's the mini displayport monitor that is causing the issues.

A little more detail on my specific setup.
Connected to 
[**_This Card_**]("http://www.sapphiretech.com/presentation/product/?cid=1&gid=3&sgid=1037&lid=1&pid=973&leg=0")
is a generic LCD via VGA->DVI,
an Auria TV connected via HDMI,
and another generic (Benq) LCD connected via VGA->mini displayport.

With the Benq disconnected, the terminal is perfect. I tested other combinations of monitors. This is the only one that failed. Now I'm unsure how to proceed. Can this still be an AMD driver issue? 

Another bit of information.. I've had to go into recovery mode once or twice in the past week or so. Not once did it give me an issue with terminals. So, it would seem that I've answered my own question above, possibly. In that case is this where I go on AMD's site and plead for a fix, or can I do something about it?

---

### Post by Tralce on 2013-02-06
> **Arith said:**
> Another bit of information.. I've had to go into recovery mode once or twice in the past week or so. Not once did it give me an issue with terminals. So, it would seem that I've answered my own question above, possibly. In that case is this where I go on AMD's site and plead for a fix, or can I do something about it?

This leads me to believe it's a driver issue. Not many drivers are loaded in recovery mode, and certainly not a proprietary AMD driver. If I'm right, then there really isn't a lot you can do about it, apart from maybe connecting a different display to that output on your card, and seeing if it works then.

---

