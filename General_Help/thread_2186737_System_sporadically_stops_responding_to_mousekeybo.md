---
title: "System sporadically stops responding to mouse/keyboard input (Rat5 mouse?)"
date: 2013-11-08
forum: General Help
---

### Post by nexis12 on 2013-11-08
Hi, 
I just installed xubuntu 13.10 from USB, while running it live everything seemed to work (used firefox while installing), 
but after restarting and booting from HDD my problems started.

xubuntu boots fine, logging in works too, but at this point it's getting weird.
Random(?) parts of Xfce start ignoring mouse/keyboard input after some seconds, this is hard to describe since it's always different parts.

First, the window management stopped working,  I couldn't resize/move/close windows or set the focus to another window by clicking.
I can still switch through windows by <power>-tabbing, but I can't interact with the window content. Switching between desktops/Opening the right-click context menu also stopped working.
The Xfce top bar sometimes partially worked at this point, for example clicking on my username would open the connected menu. On the other side, clicking the top left apps/settings button didn't worked.

After clicking around a bit, the top bar fully stopped working but moving windows started working again for some seconds, now I'm left at a point where everything is frozen.

I know that the mouse keyboard is working because I still can open the terminal via <power> t and mark text inside of it.
Interacting with the terminal works because the focus is set to it when it get's started. I can also close it using exit.

I allready had similar Problems when I tried Ubuntu/Unity a few months ago, so the problem doesn't seem to be fully Xfce related but more low level. (xserver/video driver?)
Since I'm really new to linux/*buntu, I'm not sure what to do to locate the problem at this point.
I don't get any error messages.
Thanks in advance :)

Hardware:
Sony Vaio VPCEB2Z1E
[http://www.sony.de/product/vaio-e-serie/vpceb2z1e-bq](http://www.sony.de/product/vaio-e-serie/vpceb2z1e-bq)
[COLOR=#000000][FONT=arial]Intel® Core™ i5-430M
4 GB [/FONT][/COLOR][COLOR=#000000][FONT=arial]DDR3 SDRAM
[/FONT][/COLOR][COLOR=#000000][FONT=arial]500GB HDD (100GB Partition)
Resolution: [/FONT][/COLOR][COLOR=#000000][FONT=arial]1366 x 768
[/FONT][/COLOR][COLOR=#000000][FONT=arial]ATI Mobility™ Radeon® HD 5650
[/FONT][/COLOR]
Some other information which might be useful: 
lspci -nnk | grep -i VGA -A2
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI]
Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M] [1002:68c1]
Subsystem: Sony Corporation Mobility Radeon HD 5650 [104d:9071]
Kernel driver in use: radeon

Edit: I just installed amds fglrx drivers, it didn't fixed the problem.

[SIZE=4]Edit2: I just noticed that this problem is only occuring while my mouse (cyborg Rat5) is plugged in, even if I'm using the trackpad.
I also found this solution:[/SIZE]
[http://askubuntu.com/questions/218152/ubuntu-12-10-12-04-1-lts-mouse-freezing-saitek-cyborg-r-a-t-5-mouse](http://askubuntu.com/questions/218152/ubuntu-12-10-12-04-1-lts-mouse-freezing-saitek-cyborg-r-a-t-5-mouse)
I will try it now.

Edit3:
Remapping the mouse buttons using this config really fixed the problem. Can't believe it was _that_ simple, I just wonder why this still has to be done manually.
```
[FONT=Ubuntu Mono]# Filename: 20-cyborgrat5.conf[/FONT]# Should be added into folder:
# [Fedora] /etc/X11/xorg.conf.d/
# [Ubuntu] /usr/share/X11/xorg.conf.d/
Section “InputClass”
    Identifier “Mouse Remap”
    MatchProduct “Saitek”
    MatchDevicePath “/dev/input/event*”
    Option “ButtonMapping” “1 2 3 4 5 6 7 8 9 10 11 12 0 0 0&#8243;
    # CHANGFE THE 8 AFTER 7 BACK INTO A 2 IF IT BREAKS. [FONT=Ubuntu Mono]EndSection[/FONT]
```

---

