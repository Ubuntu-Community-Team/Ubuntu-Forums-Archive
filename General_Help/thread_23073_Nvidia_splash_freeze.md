---
title: "Nvidia splash freeze"
date: 2005-03-31
forum: General Help
---

### Post by Bo Rosén on 2005-03-31
I've been unable to get the nvidia drivers working on Hoary. Everything updated to latest with k7 kernel. I've run sudo nvidia-glx-config enable.
When I restart X the Nvidia splash appears with a cursor and then nothing.
Suggestions?
Nvidia 4 440 mx, AMD 1 gHz Athlon.
Cheers,
Bo

---

### Post by Pausanias on 2005-04-06
Having a similar problem with Quadro FX 1400 Go.

GDM loads. I type in my user name and password. Then it freezes: brown screen plus cursor. I can still move the cursor, but nothing else happens.

---

### Post by Bo Rosén on 2005-04-06
Everything's working fine for me now after the last few updates.

---

### Post by Pausanias on 2005-04-06
OK I fixed the problem. Switching from nv to nvidia fixes everything.

Took me about 7 hours to figure this out. That stinking nv driver is a piece of junk. I'm all for free-as-in-speech, but sometimes it's just not worth it.

This is what I did:

1) Install hoary

2) Run the safe-mode kernel from grub

3) apt-get install nvidia-glx

4) replace "nv" in /etc/X11/xorg.conf with "nvidia"

5) reboot as normal.

Die, stupid nv driver. Die!

---

