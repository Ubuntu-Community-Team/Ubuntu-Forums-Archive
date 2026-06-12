---
title: "can I save my xorg config somewhere other than /etx/X11?"
date: 2017-09-24
forum: General Help
---

### Post by The musmula on 2017-09-24
Hello there

I have a somewhat special problem here. I'm using Ubuntu 16.04 on an xps 15 9560 running proprietary nvidia drivers. My issue is that I have a mad catz rat3 mouse which needs special configuration to work. I need to add this bit to /etc/xorg.conf
```

Section "InputClass"
    Identifier "Mouse Remap"
    MatchProduct "Madcatz Mad Catz R.A.T.3 Mouse"
    MatchDevicePath "/dev/input/event*"
    Option "ButtonMapping" "1 2 3 4 5 0 0 8 9 0 0 0 0 0"
EndSection

```

The problem is that if I enable the nvidia gpu, xorg.conf gets completely replaced (the old config gets saved with a suffix, like xorg.conf.09092017) which I thought of as annoying so I figured I'll just write a script that'll append my mouse conf to the file and run that every time I switch gpus. Except the file doesn't survive a reboot. Logging out and back in is fine but rebooting isn't.

Thanks for your attention, here's a PotatOS
[IMG]https://i.imgur.com/rBnYmXt.jpg[/IMG]

---

### Post by mc4man on 2017-09-24
Some info that may prove useful to anyone helping you is what do you mean by  'I switch gpus" 

If this is a hybrid machine (nvidia optimus) then when you switch to the Intel iGPU /etc/X11/xorg.conf must be moved to a backup or the bootup/login on Intel would fail.
When switching back to nvidia then a new xorg.conf is created as the nvidia gpu needs it.

Is this your situation or something else?
If this is your situation then what do you do about your mouse when on the Intel iGPU?

(- /usr/share/X11/xorg.conf.d is where some .conf's can be efffective though not the one for nvidia..

---

### Post by efflandt on 2017-09-24
X does not normally need xorg.conf which could be changed or moved to a backup file at any time by certain things. And where to put changes to xorg.conf is not intuitive. Instead of trying to modify /etc/X11/xorg.conf, create a file in /usr/share/X11/xorg.conf.d/ with whatever custom xorg.conf settings you want. For example this is a file I added to set coolbits to be able to alter some Nvidia speeds from NVIDIA X Server Settings:```
~$ cd /usr/share/X11/xorg.conf.d

/usr/share/X11/xorg.conf.d$ cat coolbits.conf
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Coolbits" "12"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

But you would just add section and settings specific to your mouse to use for either graphics.

---

### Post by mc4man on 2017-09-25
> **efflandt said:**
> X does not normally need xorg.conf which could be changed or moved to a backup file at any time by certain things. And where to put changes to xorg.conf is not intuitive. Instead of trying to modify /etc/X11/xorg.conf, create a file in /usr/share/X11/xorg.conf.d/ with whatever custom xorg.conf settings you want.
I *think* an exception to that would be if using nvidia drivers via nvidia-prime. Then a somewhat specific xorg.conf is needed for the nvidia driver but can't be there when using the intel iGPU

---

### Post by The musmula on 2017-09-28
mc4man, yep that is my situation, you're also right about nvidia-prime. My mouse derps around with both GPUs

efflandt, I did that and it works :D Thanks man

---

