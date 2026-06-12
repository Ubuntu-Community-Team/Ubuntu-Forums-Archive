---
title: "Kubuntu 6.06 issues (screensaver, hotkeys, kcron, Ark part)"
date: 2006-07-01
forum: General Help
---

### Post by Mguel on 2006-07-01
I'm having lot's of "little" annoying problems with my kubuntu 6.06 :( which previously didn't have on kubuntu 5.10[INDENT]1. kscreensaver doesn't lanch

2. I can't make keyboard shortcuts to work to start applications: i.e ksnapshot, kaffeine, etc. I can though ie give a shortcut to "Switch desktop", but if I associate even the same shortcut with ksnapshot it doesn't work. (The combinations is recognized on the shortcut setting window so it's not a problem of correct keyboard layout)

3. Can't get mouse gestures to work (Input actions: Gestures on Hotkeys). I think that this worked when just installed kubuntu but sometime stop working... ¿maybe when updating to KDE 3.5.3?

4. Can't make kcron run a bash file which launched a graphical application (it worked on 5.10)
```
#!/bin/bash
set DISPLAY=:0.0
export DISPLAY 
exec kwrite | aplay -q /home/user/Ding.wav
``` 
It plays the Ding.wav file (so cron is working), but doesn't run the kwrite or other app (my intention is to use it to run a windows little app through wine)

5. Can't make kcron to clean klipper history with the following command: ```
dcop klipper klipper clearClipboardHistory 
``` 
6. Can't make konqueror to show embedded compressed files (can't find Ark part). I have installed konq-plugins without getting to see Ark part
[/INDENT]The most frustrating thing is that I didn't have any problems to do this with Kubuntu 5.10 (installed Ubuntu 5.10, then installing Kubuntu-desktop)

I've searched for solutions but haven't been able to fix these things. I would apreciate any help... 

Thanks in advance,
Mguel

PS: Using Kubuntu 6.06 (clean install of Kubuntu), KDE 3.5.3

---

### Post by Jucato on 2006-07-01
I can only help with #6 (the Ark part problem)

1. Open up Konqueror and go to /usr/share/kubuntu-default-settings/kde-profile/default/share/mimelnk/application/
2. Either delete everything there or move them somewhere in your /home directory I prefer to copy them elsewhere, just in case I want them back. The FAQ recommended deleting them. Remember you have to actually remove or move those .desktop files. So you have to need root access.
3. Restart Konqueror

If you decided to just remove them, here's the easier way

From [http://www.kubuntu.org/faq.php#konqueror](http://www.kubuntu.org/faq.php#konqueror)
> 
To enable Konqueror to open tar and zip files:
```

rm -r /usr/share/kubuntu-default-settings/kde-profile/default/share/mimelnk/application/

```

Hope that helps. I'm not familiar with the other issues.

---

### Post by Mguel on 2006-07-03
[quote=Fenyx]I can only help with #6 (the Ark part problem)...
/usr/share/kubuntu-default-settings/kde-profile/default/share/mimelnk/application/
2. Either delete everything there or move them somewhere[/quote] 
Thanks!

One problem less ;)

---

### Post by Mguel on 2006-07-05
[quote=Mguel]2. I can't make keyboard shortcuts to work to start applications: i.e ksnapshot, kaffeine, etc. I can though ie give a shortcut to "Switch desktop", but if I associate even the same shortcut with ksnapshot it doesn't work. (The combinations is recognized on the shortcut setting window so it's not a problem of correct keyboard layout)[/quote]

I've continued the testing and it's as I said, the command shortcuts aren't working while the "Shortcut Schemes" (Global sh, sh sequences, Applications sh) work with no problem.

Something I notice now, that maybe can help is that I can assing the same shortcut to two programs (ie: kate and kaffeine) without getting any warning message (which I get if trying to do that at the Global shortcuts for instance

---

### Post by ScoobyDan on 2006-07-05
Mguel,

I have the same problem as you with regard to the screensaver. When I first installed Kubuntu 6.06 (a fresh install, rather than an upgrade), the screensaver worked fine. For some reason, it hasn't worked for the last couple of weeks or so.

The power management part is working though, as the screen turns off after the correct length of inactivity. :confused: 

Sorry I couldn't be of more help, but at least you now know you're not the only one...

---

### Post by Mguel on 2006-07-05
> **ScoobyDan]I have the same problem as you with regard to the screensaver. When I first installed Kubuntu 6.06 (a fresh install, rather than an upgrade), the screensaver worked fine. For some reason, it hasn't worked for the last couple of weeks or so.

The power management part is working though, as the screen turns off after the correct length of inactivity. :confused: 

Sorry I couldn't be of more help, but at least you now know you're not the only one...[/quote] 
 said:**
>     4. Can't make kcron run a bash file which launched a graphical application (it worked on 5.10)
    ```
#!/bin/bash
    set DISPLAY=:0.0
    export DISPLAY
    exec kwrite | aplay -q /home/user/Ding.wav
```     It plays the Ding.wav file (so cron is working), but doesn't run the kwrite or other app (my intention is to use it to run a windows little app through wine)

    5. Can't make kcron to clean klipper history with the following command: ```
dcop klipper klipper clearClipboardHistory 
``` 

Both of which where working with the same commands on kubuntu 5.10

Thanks,
Mguel

---

### Post by Mguel on 2006-07-08
After restarting my pc, khotkeys didn't work anymore (although it's running).

Killed it and started it from konsole and got the following error:
```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
``` 
So maybe this has to do with a problem with my xorg.conf when configured the nVidia TV-Out accorging to:
[http://www.ubuntuforums.org/showthread.php?t=98456](http://www.ubuntuforums.org/showthread.php?t=98456)

Edit: reboot with my old xorg.conf (before setting TV-out) and khotkeys work fine... so probably there is the problem... but I don't know how to solve it :( 
(Forgot to test kscreensaver and klipper problem from kcron but maybe they are also related to the same thing)

---

### Post by Mguel on 2006-07-16
OK, trying and trying ](*,)  I found a way to have khotkeys working using the xorg.conf with tv-out enabled.

I kill khotkeys and run:
```
khotkeys --display :0.0
``` I get the following error message:
```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
$ X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
``` But khotkeys start working (keyboard shortcuts and mouse gestures).

I made a shortcut on my Autostart folder with the following command:
```
killall khotkeys | khotkeys --display :0.0

``` and I have it working automatically...

I would appreciate any one that could help me as to make it the "correct" way (without the error message).

Another option would be instead of having to kill the hotkeys with the autostart link first, would be to add the command line (--display :0.0) where ever khotkeys is launched at the first time (on kde startup process). But I don't know where this could be :confused: ... any clue?

Cheers,
Mguel

---

