---
title: "Do you have flash player? Want to help someone in need?!"
date: 2005-04-20
forum: General Help
---

### Post by ming0 on 2005-04-20
I need some help figuring out if my computer is the problem, or if there is yet another linux/flash bug. My desktop has more than enough power to play a simple flash file (P4 3.2E) and am running Hoary, Firefox 1.0.2, and have the flash plugin 7.0.25.0.

When I play this flash animation, every time the sound plays, there is a clipping noise at the end--and the animation stops momentarily too. I have a laptop (PIII 866MHz) with virtually the same software set (Ubuntu Hoary, Firefox 1.0.2), and the animation and sound work perfectly. I even deleted the plugin from my desktop and copied the flash player plugins from my laptop onto my desktop, and still have the same problem.
 
Oddly enough, I can get the problem disappear temporarily. If I open the settings box, and switch to the mic tab, the little meter will stay blank, but if I switch through a few of the tabs, and go back to the microphone tab, I will suddenly see the meter start monitoring the sound level, and the clipping (and animation) problem ceases to exist. However, as soon as I shut the settings dialogue, the clipping problem resumes.
 
 The animation is at: [http://www.notthemessiah.net/flash-test/]("http://www.notthemessiah.net/flash-test/")

Please give me feedback, and let me know if it's my computer or if it's my animation. 

Thanks in advance :)

Edit: I tried watching this in Opera too, and had the same problem

PS-**please post here if it works properly**, that way I'll know if there is an actual bug, or if this is just an anomaly.

---

### Post by ming0 on 2005-04-21
I suppose I wasn't specific enough about the animation--sound begins after about 5 seconds (it begins *very* subtly), and[b] the actual animation takes about 12 seconds to start.

[/b]Please watch the animation (it will take you less than 20 seconds to see if it's working properly). Just make sure you **turn your sound up** to 60-90%.

I will really appreciate it if I get a few positive or negative responses here!

Thanks in advance :)

(bump)

---

### Post by StacyWebb on 2005-04-21
Flash runs fine, I would check you alsa drivers (for sound). I guess the next question is do you have any problem with  playing audio files?

---

### Post by ming0 on 2005-04-21
My sound server seems very healthy--**I can have 2 different flash animations and beep media player all playing at the same time.** I also play UT2004, and the sound works okay there too.

This problem is really getting annoying. This animation is part of my portfolio, and if I submit it and it *happens* to not work on the viewer's computer, I am screwed ](*,)

(plus I try to make everything as linux friendly as possible)

---

### Post by StacyWebb on 2005-04-21
It worked fine on this end, so I would say if you submitted it to someone they would most likley not have a problem with it either.

---

### Post by zwaardmeester on 2005-04-22
I'm using Opera, and I had similar problems. I solved it as follows:

1) locate libXm.so

this will return your libXm version, there is a 1, 2 or 3 somewhere in it's path. Remember that value.

2) cd /usr/lib/opera/plugins

3) sudo mv ./operamotifwrapper-N ./operamotifw_unused-N

rename all operamotifwrapper-N files where N is not your libXm version. So you need only 1 of these files.

4) make sure you have the plugin installed (flashplayer.xpt & libflashplayer.so files)

---

