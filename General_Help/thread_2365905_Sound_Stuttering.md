---
title: "Sound Stuttering"
date: 2017-07-12
forum: General Help
---

### Post by jim_deadlock on 2017-07-12
When I'm playing a video game, watching youtube or anything, my sound flickers off every few seconds and it's really annoying. I dual-boot Win10 and the same games/videos are fine there, so I can rule out a hardware problem. I've also tried killing pulseaudio (after disabling autospawn) and playing the same videos in Chromium via ALSA - same issue. This has only just started happening so I tried booting with the previous kernel, still no joy...

---

### Post by jim_deadlock on 2017-07-14
This forum used to be so active, I can't believe nobody has even viewed my post in 2 days :(

EDIT: welp... I've been messing around with my BIOS and the problem seems to have fixed itself. Don't know exactly how. Could have been when I removed my CMOS battery for a bit. I'm still scratching my head over why it didn't affect Windows but never mind.

Before it fixed itself I noticed an intermittent quiet popping noise in my speakers as if some background process was sending signals or something. Just thought I'd mention it in case anyone cares...

---

### Post by psychedelian87 on 2017-08-16
Hello there, thank you for this thread. I am also surprised at your lack of responses as would of assumed this is a fairly common issue. I've been bearing with this for a while but think I've established the actual reason for it, and how to correct it.
I must note that I'm brand new to Linux, this is my third day using Ubuntu; so anything I have to contribute to this website will be far less knowledgeable than most other users posting on here. However, I'm pretty sure I've nailed this. The stuttering was a literal stutter in which videos would stop and make a 1 second repetition of the audio before carrying on. Really annoying, bareable for some maybe but a deal breaker for me.

I thought it was a driver issue so went about using a proprietary driver from AMD, which didn't work. I performed a sudo install of flash. No change. I did a sudo install of ubuntu restricted extras. No change. I trailed forums for a good 4 hours straight, picking up bits of information and trying various things that seemed logical, much to no avail. 
After burying my head into the Ubuntu 17.04 manual, I came across some information regarding 'Swappiness', and reading how that worked immediately brought to mind Windows 10's 'Superfetch' and how that slowed my system down. Swap space is an area that combines with your RAM to hold inactive memory pages temporarily. I wanted to see how much RAM was being dedicated to this, and then reduce it to see if that was causing any problems. Low and behold, I've identified and fixed the problem.

[U][B]FIX FOR STUTTERING YOUTUBE VIDEOS/LAGGING ISSUES IN UBUNTU 17.04
[/B][/U]
**1.*** Check your current swappiness filesize, which is usually 60 by default in Ubuntu 17.04, by entering Terminal and typing: *

cat /proc/sys/vm/swappiness

**2.*** Open the following config file in a text editor e.g. gedit:*

gksu gedit /etc/sysctl.conf
[B]
3.[/B] [I]In the text editor, scroll down to the end of the file and enter the following (I decreased mine to 10, but you could go to zero; in which case swap files will only be used when absolutely necessary):
[/I]
#
# Decrease swappiness value
vm.swappiness=10

[I]Save the file, then restart your computer. 

[/I]And that's it, done. You can check your current swappiness value by going back into Terminal and re-entering "cat /proc/sys/vm/swappiness", and set it to whatever value you like by using the above method. 

This has completely sorted the browser stuttering out for me, so I can only assume this is the reason for it and now declare this a solution for all.


Power to ye.

---

### Post by jim_deadlock on 2017-08-16
Thanks for the reply. Unfortunately what you've described is something I always do immediately whenever I install Ubuntu, so I already had vm.swappiness=10 when I was having this issue. I'm glad it cleared it up for you anyway. I've not encountered the issue before or since, so it'll remain a mystery to me.

---

### Post by psychedelian87 on 2017-08-18
That is really bizarre. Another thing I have done is to enable a proprietary graphics driver, in the additional drivers of the 'software & updates' tab, which may of contributed to resolving the issue. I don't have flash installed either.. do you?

---

### Post by jim_deadlock on 2017-08-18
I always have proprietary driver and flashplugin-installer

---

### Post by psychedelian87 on 2017-08-18
Try dropping the flashplugin? Perhaps try the Opera browser too.

---

### Post by jim_deadlock on 2017-08-18
Like I said, I no longer have this problem, it disappeared and it's been fine ever since.

---

### Post by psychedelian87 on 2017-08-19
Fair play mate.

---

### Post by vasa1 on 2017-08-19
> **jim_deadlock said:**
> This forum used to be so active, I can't believe nobody has even viewed my post in 2 days :(
...
Sadly, there is a problem with view counts. They are broken and I can't say when the issue will be fixed.

---

### Post by jim_deadlock on 2017-08-19
Well to me that's good news, it means people are still here :)

---

### Post by vasa1 on 2017-08-22
And I just noticed that there's a line at the bottom of the page with "Members who have read this thread in the last 30 days: 10". I don't know how long that feature's been there!

---

### Post by jim_deadlock on 2017-08-22
Must be a moderator feature, I don't see that - although I'm assuming it's the same number that's shown as 'views' on the main forum list.

---

### Post by vasa1 on 2017-08-22
> **jim_deadlock said:**
> Must be a moderator feature, I don't see that - ...
You may be right. If I don't sign in I don't see it, but on another vBulletin forum where I'm most certainly not a moderator, a similar line is visible.

---

