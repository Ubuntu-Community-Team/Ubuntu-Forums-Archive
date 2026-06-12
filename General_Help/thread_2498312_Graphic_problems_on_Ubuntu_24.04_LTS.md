---
title: "Graphic problems on Ubuntu 24.04 LTS"
date: 2024-06-08
forum: General Help
---

### Post by francreeper03 on 2024-06-08
Hello,

I've recently installed Ubuntu on my machine. I have several graphical problems on my system:
- **Phantom display**
  I've already solved this by turning it off via xrandr, but I found it weird as I only have one HDMI display connected. This display caused my mouse to go off-screen or to open invisible windows.
- **High frame time**
  I am a game developer, and I use Godot 4 game engine. I experienced several bugs that I didn't have on Windows before. One of these is pretty annoying and is the high frame time, in fact some frames reach 50ms during mouse click input. I profiled my code and the problem is not there. I noticed it must be an issue with the driver or the compositor when I used fullscreen instead of windowed. The problem doesn't happen in fullscreen mode. I wanted to use another compositor and this brings us to the next problem:
- **Unstable Ubuntu on Wayland**
  I tried to switch to Wayland, but the windows are for some reason undecorated and severely unstable graphically, glitching, and the archive app doesn't open and crashes. I can't find a solution to this problem.

[B]My machine:
[/B]My hardware may not be the newest, but it worked fine on Windows:
HW model: Micro-Star International Co., Ltd. MS-7B19
CPU: Intel® Core™ i3-8100 × 4
Memory: 16GB
My system is installed on a 250GB SSD and I have an external 1TB HDD.

[B]What I tried:
[/B]I disabled the phantom display and it doesn't annoy me anymore. Wayland doesn't work. Is there another compositor I can try, or maybe how do I make Wayland work correctly? I tried reinstalling the graphic drivers, and even different versions, but nvidia sucks on Linux I guess, so it didn't change (reinstalling them by command messed it up even more, that it didn't even detect HDMI).

Thank you in advance.

---

