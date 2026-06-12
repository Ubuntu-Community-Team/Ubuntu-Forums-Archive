---
title: "Intel UHD Graphics 620 issues on 18.04.4 LTS"
date: 2020-03-14
forum: General Help
---

### Post by ilya31 on 2020-03-14
Hi, everyone!

Just got a new laptop (Latitude 7400-2675) with pre-installed Ubuntu 18.04 on it. 
Being a lifelong Windows user I initially wanted to get Windows 10 on it, but decided to try this one out as it turned out to be quite neat for my taste.

Anyway, there is a tiny issue that doesn't let me enjoy my purchase 100%.
The thing is, _when I watch a YouTube video_ with *quick* camera movements, _it tends to have some kind of horizontal tear/deformation_ usually in the upper third of the screen resulting in horizontal lines.
In other words, during dynamic shots\scenes on YouTube one part of the video is moving a bit faster than the other and you can see that on the display. 
When the camera is stable and not moving, the video playback works relatively fine.

My guess is this is somehow connected to me not being able to find the proper Intel UHD Graphics 620 driver though I did update the system to the latest version.
Or maybe this is the result of my RAM working in a single-channel mode as opposed to the dual-channel one, which is said to be better for integrated graphics... (one of the 2 RAM slots is empty, the other has 8Gb DDR4-2400)

As a Ubuntu newbie I am not so sure how to fix this one, so any response will be much appreciated!
[B]
update:[/B]
could this be the solution?
[https://www.youtube.com/watch?v=IJeX35wbZY4](https://www.youtube.com/watch?v=IJeX35wbZY4)

---

### Post by ipv on 2020-03-14
i have never experienced screen tearing with ubuntu nor with neon which is an ubuntu derivative, but on the same machine with the latest debian buster i faced screen tearing with both mpv & vlc.

the solution in the youtube link you have posted did solve the screen tearing problem for me.

---

### Post by speartip on 2020-03-16
The fix in your link is the one I use for tearing on Intel Graphics.
You can try it, it won't do any harm and you can always delete the file if it doesn't work.
Run the following in a terminal:
[SIZE=2]```
[FONT=Cantarell]sudo gedit /usr/share/X11/xorg.conf.d/20-intel.conf[/FONT]  
```
Then copy & paste the following in the empty file that opens:
[/SIZE]```
[LEFT][SIZE=2] [FONT=Cantarell]Section "Device"[/FONT][/SIZE]
[SIZE=2] [FONT=Cantarell]Identifier "Intel Graphics"[/FONT][/SIZE]
[SIZE=2] [FONT=Cantarell]Driver "intel"[/FONT][/SIZE]
[SIZE=2][FONT=Cantarell]Option "TearFree" "true"[/FONT][/SIZE]
[SIZE=2] [FONT=Cantarell]# Option "AccelMethod" "sna" [/FONT] [/SIZE]
[SIZE=2] [FONT=Cantarell]# Option "AccelMethod" "uxa"[/FONT][/SIZE]
[SIZE=2] [FONT=Cantarell]EndSection[/FONT]
[/SIZE][/LEFT]

```[SIZE=2]
Then Reboot the computer.

[/SIZE]

---

### Post by GhX6GZMB on 2020-03-16
IIRC, the browser under Ubuntu comes with hardware acceleration disabled. If you enable acceleration, this might solve the problem.

---

