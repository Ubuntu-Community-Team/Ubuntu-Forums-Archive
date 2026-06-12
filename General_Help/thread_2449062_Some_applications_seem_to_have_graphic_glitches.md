---
title: "Some applications seem to have graphic glitches"
date: 2020-08-19
forum: General Help
---

### Post by ludwig015 on 2020-08-19
Hi!
I'm using Ubuntu 18.04 and since today I get some graphic glitches on some of my applications.

I guess they appeared because of the ```
sudo apt upgrade
``` I did yesterday. (Only a guess...)
I have never updated my programs like this since I installed Ubuntu (april, this year); I usually updated them manually with ```
sudo apt install [pkg]
```
And therefore the *apt upgrade* updated a lot of programs.

The programs on which I found these glitches were on the **Godot Game Engine **and on **OpenMW (Morrowind - Game)**.
In Godot, the icons in the project manager are glitched and the hover text bubble does have a glitched font.
In OpenMW/Morrowind the title screen and in-game visuals are glitched (i cannot show these because I somehow cannot add a forth attachment).

I have no idea why they appeared and more important have no idea how to get rid of them.

I appreciate every help I can get, thanks!



[ATTACH=CONFIG]286763[/ATTACH][ATTACH=CONFIG]286764[/ATTACH][ATTACH=CONFIG]286765[/ATTACH]

---

### Post by TheFu on 2020-08-19
**sudo apt update ** has to be run first or you risk getting incompatible libraries.

Issues with game graphics aren't odd. The game makers often don't use the correct calls as intended as they try to make the frame rates as quick as possible.

The first questions are:
[LIST]
[*]Are you using X11 or Wayland?
[*]Are you using the proprietary GPU driver or the F/LOSS GPU driver for your card?
[/LIST]
Running
```
$ inxi -GC
```
will answer those questions.

---

### Post by ludwig015 on 2020-08-19
I'm 90% sure that I've used sudo apt update before sudo apt upgrade.

I am using X11 and the output of the command says:
```
CPU:       Dual core AMD Athlon 3000G with Radeon Vega Graphics (-MT-MCP-) 
           cache: 1024 KB
           clock speeds: max: 2157 MHz 1: 2001 MHz 2: 1717 MHz 3: 2157 MHz
           4: 1727 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Picasso
           Display Server: x11 (X.Org 1.20.8 ) driver: amdgpu
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: AMD RAVEN2 (DRM 3.35.0, 5.4.0-42-generic, LLVM 10.0.0)
           version: 4.6 Mesa 20.0.8
```

---

### Post by dragonfly41 on 2020-08-19
> [COLOR=#000000]I'm 90% sure that I've used sudo apt update before sudo apt upgrade.
[/COLOR]You can check history of past commands by running in terminal ...
```
history
```

---

### Post by ludwig015 on 2020-08-19
Oh, thanks, I forgot. :|
Yes, I have used sudo apt update just before sudo apt upgrade.

---

### Post by TheFu on 2020-08-19
I'd try using Wayland.  On the login screen, click the "gear" and select "Wayland", then login as normal.

---

### Post by ludwig015 on 2020-08-19
I tried Wayland, which causes same behavior in Godot and on OpenMW I get a crash and error:

"*Failed to create SDL Window: Couldn't find matching GSX Visual*"

---

