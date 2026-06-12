---
title: "No hdmi audio after resume from suspend"
date: 2014-11-05
forum: General Help
---

### Post by splintr on 2014-11-05
Hi,

I'm running Ubuntu 14.04 LTS with gnome 3 and xbmc, it is connected to my LG tv over hdmi.

When the system is off and i turn it on, everything works perfect, audio and video over hdmi, when my system suspends to s3 the problems start.
On resume there is no audio over my hdmi, and when i try to detect display settings or log out, my screen turns black.

i've tried:

- unplug/pluggin in the hdmi
- "sudo alsa force reload"

But nothing seems to work. The only thing that works is to restart my system, then everything is working cool. Until it is suspended again.
i've Googled it and searched for it, saw a lot of topics with some kind of same problem but no solution.

---

### Post by stanton on 2014-11-07
I have no solution, but only a workaround for now.

From the black screen:
Ctrl-Alt-F1
login
sudo service lightdm restart
(on mine I have to then kill the mythfrontend.real because it's pegging the processor)

This is my mythtv HTPC, and the wife is not all that happy about the upgrade to 14.04.

---

### Post by justen_m on 2014-11-07
I don't know if this will help or not... I went through a somewhat similar issue, but no HDMI involved.

When my HP Z400 workstation woke from suspend, there was NO audio at all.
lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller

I could manually fix this by muting the sound, unmuting the sound, and then changing the volume. ALL steps were required. Muting and unmuting wasn't enough. I had to change the volume afterwards. Now, instead of doing this manually, I made the following change... I created a file in /etc/pm/sleep.d and put the following in it (name of the file doesn't matter, everything in that directory will be executed upon waking from sleep (and hibernate, I think)). Type amixer on the command line to see if you have a control for HDMI. I just have basic sound.

#!/bin/sh
# put this in a file in /etc/pm/sleep.d/
# make sure the file is executable
# fixes problem on hpz400 of no sound after resume from sleep

/usr/bin/amixer set Master mute
/usr/bin/amixer set Master unmute
/usr/bin/amixer set PCM unmute
/usr/bin/amixer set Speaker unmute
/usr/bin/amixer set Headphone unmute
/usr/bin/amixer set Master 2dB+

---

### Post by pqwoerituytrueiwoq on 2014-11-07
what video card are you using?
i have a issue with this, but it is worse (also loose my display) but it only happens if my TV is off when i wake from suspend
i have to restart lightdm and reload alsa to get it fixed or reboot
i assume you are using hdmi

---

### Post by splintr on 2014-11-08
Hi Thanks for the reply guys.

Still no working solution, I've tried to restart the display manager but that doesn't work -> Screen Black (tv says no signal)
i've tried the solution from juster_m still no sound after those commands.

i'm using my integrated video card on my board Asus P5G41-M.
Only solution that works is to restart the whole system, but that isn't cool for my 24/7 htpc / homeserver

but thanks for the answers guys

---

### Post by pqwoerituytrueiwoq on 2014-11-08
not sure if it helps you but i managed to get a little progress
i can now recover my GUI with my keyboard after doing some config in xorg.conf sounds remains broken, but i no longer loose my saved sata and can close firefox safely (not crash it my killing it when lightdm restart)
[http://ubuntuforums.org/showthread.php?t=2200907](http://ubuntuforums.org/showthread.php?t=2200907)
once i did that i was able to use [FONT=courier new]xrandr --output HDMI-0 --auto[/FONT] via hot-key and it bring the display back online

---

### Post by splintr on 2014-11-16
Hi,

i've tried your solution and it also doesn't work.
Almost tried everything that's in my knowledge, and still can't find a solution.
It is so annoying to restart every time is need it, to watch a movie/youtube or whatever with sound.

Is there a previous ubuntu version or beta (or anything that is based on debian) where it does works?
If it fixes the problem, i will reinstall the whole server and everything to fix this problem.

---

### Post by pqwoerituytrueiwoq on 2014-11-16
fond this:
[http://ubuntuforums.org/showthread.php?t=1147885](http://ubuntuforums.org/showthread.php?t=1147885)
Leads here:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
given this is so very very old, this is probably the only part you would need
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"true" # i8xx users: see note in guide
EndSection
```

---

### Post by splintr on 2014-11-16
Thanks again for the post and the new steps.

i've tried it, read the whole 2 threads, edited xorg.conf, generated a new one, tried other tweaks.
Still when i logout or use control+alt+F* buttons i still lose my display.
The audio is still gone after suspend resume, and when i try to change resolution in gdm it goes to all black.

Only way to go is to restart, each time i want to watch/hear a thing on my HTPC.
To bad but it seems that everyone has the same problem but different workarounds

---

### Post by pqwoerituytrueiwoq on 2014-11-16
perhaps fixing this is not worth the time (or annoyed wife)
you may be better off using a different budget GPU
[http://tinyurl.com/p3uoabj](http://tinyurl.com/p3uoabj) used ones on ebay look to be about $20

---

### Post by splintr on 2014-11-16
i do have a 4350 card, but it doesn't fit in my htpc/server case.
And its more power efficient when there are not a lot extra components in it.

Too bad, thanks for your time Bro !

---

### Post by pqwoerituytrueiwoq on 2014-11-16
can you use a vga and 3.5mm audio cable? maybe it will stop acting up then
vga can do 1920x1080 res if the cord is short

---

### Post by splintr on 2014-11-17
I can try that tomorrow.

Today i've reinstalled the whole system, because i couldn't take it anymore.
Installed Ubuntu 14.04.1 with ssh server, xfce4 (this time) and Slim Login Manager, and X11VNC.

When the system is up, everything works cool.
When i go to suspend from menu, and resume, the display comes back for 3 seconds and goes to black. But when i try to connect to vnc (x11vnc) i can see my monitor on my client pc.

Xrandr tells me now hdmi is disconnected, and the only solution is to reboot again.
Isn't there a command to reinit the graphics card or something?


[Edit]
i've found a vga cable and tested the video, after suspend the video resumes on vga.
tomorrow i can test the sound, because i don't have a 3.5mm cable here.

At least it's a solution (for now :))

---

### Post by pqwoerituytrueiwoq on 2014-11-19
```
xrandr --output HDMI0 --auto
```
HDMI0 varies from system to system

---

### Post by splintr on 2014-11-19
Yes thanks i had tried that one but that also didn't get my hdmi back on.

I've tried the vga cable and a 3,5 -> red/white cable to my tv.
The video is fixed when i go to the VGA input source, but my sound doesn't work.
When i switch my tv to AV3 on my LG tv, the video is gone, screen is black but i hear the sound.

So it seems i need to restart my pc every time and use hdmi

---

### Post by pqwoerituytrueiwoq on 2014-11-19
did you set your sound config to use analog audio instead of hdmi?
```
pavucontrol
```

---

### Post by splintr on 2014-11-19
Yes sir !
I got sound on my tv but no video.
or video without sound.

vga = video without sound
av3 = sound without video

too bad

---

### Post by pqwoerituytrueiwoq on 2014-11-19
with vga do headphones work (in the rear port), it may be a setting on your tv
you did unplug the hdmi when using vga right
can you try dvi to hdmi (hdmi 1 is usually the one with dvi support, aka 3.5mm audio support) + analog?

---

### Post by splintr on 2014-11-22
Hi,

I've found out that vga only works with 3.5mm next to the vga port on the tv, didn't know about that.
Now i have sound and video with vga and 3.5mm > 3.5mm cable.

I've also tried the latest mainline kernel to see if the hdmi works after suspend but that isn't the case, also tried the intel display drivers installer. So it seems there isn't a working solution for hdmi  (video/audio) resume after suspend.
Too bad that it doesn't work, soon i will have my receiver.

Thanks for your knowledge,information and patience Sir !

Hope it will be fixed in the future, i will leave this topic open... Maybe in the future someone knows the real solution for hdmi

---

### Post by splintr on 2015-02-02
Still struggling with the same issue. I've updated everything, tried the expirimental stuff. Messed with xorg.conf, display managers, bios settings, bios flash. Have found a couple of other topics with the same issue with the date of 2008. So i guess it is not a priority to get it fixed. It sucks to reboot everytime i want to check a movie or something on my htpc. So the only solution is 24/7 up and running or reboot every time you need to use sound / or use vga and the 3.5mm audio cable (but now i can't anymore because my tv is on the wall, and don't got space for the vga cable)

Somebody else a solution?

---

### Post by seanos on 2015-08-22
I’ve struck this issue when trying to use the motherboard HDMI for audio only.

[SIZE=1](If I use my NVIDIA card then I can’t use my second monitor and I get a phantom monitor belonging to the receiver where programs can get launched and the mouse cursor can enter the void. If I send video *through* the receiver I lose my monitor’s native resolution of 1920 × 1200.)[/SIZE]

I’m wondering if the common factor here is Intel HDA Audio? In my case...

```
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
```

Did you find any solution to this?

---

### Post by helio4 on 2016-05-11
i have a crazy workaround. Install supertuxkart and execute it. The hdmi sound will go back instantly. So I do this every time i need hdmi sound after resuming from suspend

---

