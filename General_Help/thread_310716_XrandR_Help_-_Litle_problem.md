---
title: "XrandR Help - Litle problem"
date: 2006-12-01
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-12-01
I wanted to rotate the screen 90 degrees for my screen. I tried xrandr and this is what I get:

```

giga@ubuntuzilla:~$ xrandr -o left
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12
giga@ubuntuzilla:~$
``` ](*,)

It's a Samsung 173p plus silver  :-k

---

### Post by s_h_a_d_o_w_s on 2006-12-03
Bump

---

### Post by sedd on 2006-12-06
same:

scott@sedhp:~$ xrandr -o left
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12


lil help?

---

### Post by sedd on 2006-12-06
oops forgot: its a hp nw9440 laptop, nvidia quadro 1500M and nec 2080UX+ monitor

---

### Post by s_h_a_d_o_w_s on 2006-12-07
RE-bump

---

### Post by MetalMusicAddict on 2006-12-07
What video card are you running?

---

### Post by meng on 2006-12-07
If you haven't already done so, edit xorg.conf and add following line under Device (video card):
Option "RandRRotation"

---

### Post by MetalMusicAddict on 2006-12-07
> **meng said:**
> If you haven't already done so, edit xorg.conf and add following line under Device (video card):
Option "RandRRotation"

This is what I was getting at **IF** he's running a nVidia GFX card.

Im running a 7900GT with the drivers from the repo on Edgy. Adding **Option "RandRRotation" "on"** adds the option to rotate in nvidia-settings. It just shows up.

Screenshot [HERE]("http://img237.imageshack.us/img237/9553/screenshotzl6.png"). Warning 1200x1920 image.

---

### Post by s_h_a_d_o_w_s on 2006-12-07
So if I don't have nvidia (i don't) I can't rotate? Or can I? What do I put in xorg exactly?

---

### Post by MetalMusicAddict on 2006-12-07
Well tellin' us what you *do* have will help. ;)

---

### Post by s_h_a_d_o_w_s on 2006-12-07
Sry, i'm noobish as to cards etc. What exactly do you need to know?

---

### Post by MetalMusicAddict on 2006-12-08
You mentioned that you didnt have a nVidia GFX card. What brand/model do you have? Is this a laptop?

---

### Post by s_h_a_d_o_w_s on 2006-12-08
I don't have a video card,  turns out it's embedded video, Via Km400 northbridge chip. It's my desktop

---

### Post by s_h_a_d_o_w_s on 2006-12-08
bump

---

### Post by MetalMusicAddict on 2006-12-09
Wow. Ouch, Sorry. Via chipset? I wouldnt know where to begin. :(

---

### Post by s_h_a_d_o_w_s on 2006-12-15
Do you think if I get an nvidia video card, and I just plop it in, it'll wok ootb? Because I was thnking of getting one, would that help xrandr and beryl?

---

### Post by s_h_a_d_o_w_s on 2006-12-16
Bu/\/\P

---

### Post by toobuntu on 2007-06-22
modify /etc/X11/xorg.conf to allow for rotating the monitor (not just for nvidia, i have an intel graphics card):

1. under "Devices" section, add the following in order to have an option in 'System->Preferences->Screen Resolution' to rotate the monitor:
Option "RandRRotation"
2. or, under "Devices" section, add the following in order to automatically rotate the monitor counterclockwise upon starting X:
Option "Rotate" "CCW"
3. note: when the monitor is rotated and beryl is running, there is a SIGNIFICANT increase in latency and overall slow performance.  it is not usable for me when rotated and trying to use winxp apps in VMware.
4. note: under 'System->Preferences->Screen Resolution' there should also be a check box to make the rotation you choose there the default for the machine.

---

