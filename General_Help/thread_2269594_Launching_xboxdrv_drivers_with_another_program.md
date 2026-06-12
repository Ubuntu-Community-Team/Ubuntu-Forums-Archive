---
title: "Launching xboxdrv drivers with another program"
date: 2015-03-16
forum: General Help
---

### Post by ppas-facebook on 2015-03-16
Hey guys,

My housemate and I have been setting up a Ubuntu-based Kodi (XBMC) home entertainment system, and we've recently got stuck. Basically, what we want to do now is to make it so that we can launch Chrome and use a wireless Xbox 360 controller as a 'mouse' along with the "onboard" onscreen keyboard, and then for xboxdrv to end and for xpad to start up again when Chrome is closed.

Basically, we have all the separate parts of it working, it's just getting it into a shell script to use with Advanced Launcher in Kodi that's proving difficult.

So far, we can (separately):
Launch xboxdrv with mouse emulation and custom mappings (a button to bring up "onboard" and a combo to exit the browser)
Launch Chrome in --kiosk mode and have it work with the controller
Launch them both at the same time from a .sh file
Launch .sh files from Kodi

But: xboxdrv will not exit when Chrome does. Which is crucial, as Kodi (and Steam and other local games) all need the standard xpad driver to work best.

Also, further problems include: the script needs sudo permissions in order to rmmod/modprobe xpad (or to use --detach-kernel-driver with xboxdrv)
But: Chrome cannot be started with sudo (refuses to start, also not a good idea to run a browser as root), this means we cannot use xboxdrv's built in ability to start with programs, as it makes the whole command root (including Chrome).

Both of us are kind of Linux-savvy, but we just don't know the ins and outs of shell scripts, so could someone help us?

---

### Post by ppas-facebook on 2015-03-17
Ok, so after a bit more googling, I found this question, which is similar to what I want: [http://stackoverflow.com/questions/26480441/wait-for-a-process-launched-by-another-program-to-terminate](http://stackoverflow.com/questions/26480441/wait-for-a-process-launched-by-another-program-to-terminate)

So how would I adapt his script to run Chrome instead of the Steam game he is using? (His script below)

```
[COLOR=#00008B]if[/COLOR][COLOR=#000000][[/COLOR][COLOR=#800000]"$GAMENAME"[/COLOR][COLOR=#000000]=[/COLOR][COLOR=#800000]"BTR2"[/COLOR][COLOR=#000000]][/COLOR][COLOR=#000000]||[/COLOR][COLOR=#000000][[/COLOR][COLOR=#800000]"$GAMENAME"[/COLOR][COLOR=#000000]=[/COLOR][COLOR=#800000]"Runner 2"[/COLOR][COLOR=#000000]];[/COLOR][COLOR=#00008B]then[/COLOR][COLOR=#000000]
    APPID[/COLOR][COLOR=#000000]=[/COLOR][COLOR=#800000]218060[/COLOR][COLOR=#000000]
    [/COLOR][COLOR=#2B91AF]GameProc[/COLOR][COLOR=#000000]=[[/COLOR][COLOR=#000000]r[/COLOR][COLOR=#000000]][/COLOR][COLOR=#000000]unner2
[/COLOR][COLOR=#00008B]fi[/COLOR][COLOR=#000000]

sudo [/COLOR][COLOR=#000000]--[/COLOR][COLOR=#000000]validate
sudo xboxdrv [/COLOR][COLOR=#000000]--[/COLOR][COLOR=#000000]silent [/COLOR][COLOR=#000000]--[/COLOR][COLOR=#000000]quiet [/COLOR][COLOR=#000000]--[/COLOR][COLOR=#000000]detach[/COLOR][COLOR=#000000]-[/COLOR][COLOR=#000000]kernel[/COLOR][COLOR=#000000]-[/COLOR][COLOR=#000000]driver [/COLOR][COLOR=#000000]--[/COLOR][COLOR=#000000]mimic[/COLOR][COLOR=#000000]-[/COLOR][COLOR=#000000]xpad [/COLOR][COLOR=#000000]--[/COLOR][COLOR=#000000]dbus session [/COLOR][COLOR=#000000]&[/COLOR][COLOR=#000000] sleep [/COLOR][COLOR=#800000]2[/COLOR][COLOR=#000000]
steam steam[/COLOR][COLOR=#000000]://[/COLOR][COLOR=#000000]rungameid[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]$APPID [/COLOR][COLOR=#000000]&[/COLOR][COLOR=#000000] sleep [/COLOR][COLOR=#800000]20[/COLOR][COLOR=#000000]

check_run_and_grab[/COLOR][COLOR=#000000](){[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#00008B]if[/COLOR][COLOR=#000000] ps aux [/COLOR][COLOR=#000000]|[/COLOR][COLOR=#000000] grep [/COLOR][COLOR=#800000]"$GameProc"[/COLOR][COLOR=#000000]>[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]dev[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]null
    [/COLOR][COLOR=#00008B]then[/COLOR][COLOR=#000000]
        [/COLOR][COLOR=#2B91AF]GamePID[/COLOR][COLOR=#000000]=[/COLOR][COLOR=#000000]$[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]pgrep [/COLOR][COLOR=#000000]-[/COLOR][COLOR=#000000]x [/COLOR][COLOR=#800000]"$GameProc"[/COLOR][COLOR=#000000])[/COLOR][COLOR=#000000]
        [/COLOR][COLOR=#00008B]while[/COLOR][COLOR=#000000] kill [/COLOR][COLOR=#000000]-[/COLOR][COLOR=#800000]0[/COLOR][COLOR=#800000]"$GamePID"[/COLOR][COLOR=#000000];[/COLOR][COLOR=#00008B]do[/COLOR][COLOR=#000000]
            sleep [/COLOR][COLOR=#800000]5[/COLOR][COLOR=#000000]
        [/COLOR][COLOR=#00008B]done[/COLOR][COLOR=#000000]
        sudo killall xboxdrv
        exit [/COLOR][COLOR=#800000]0[/COLOR][COLOR=#000000]
    [/COLOR][COLOR=#00008B]else[/COLOR][COLOR=#000000]
        echo [/COLOR][COLOR=#800000]"Game process not found, waiting 5 seconds and trying again"[/COLOR][COLOR=#000000]
        sleep [/COLOR][COLOR=#800000]5[/COLOR][COLOR=#000000]
        check_run_and_grab
[/COLOR][COLOR=#00008B]fi[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]}[/COLOR][COLOR=#000000]

check_run_and_grab

[/COLOR]
```

Can I get rid of the first IF statement?
Could someone explain exactly what check_run_and_grab is doing?

---

