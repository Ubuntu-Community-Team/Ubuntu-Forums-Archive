---
title: "Harnessing Ubuntu Drivers"
date: 2014-09-24
forum: General Help
---

### Post by SJLPHI on 2014-09-24
Hello,
I have made switch from Linux Mint 17 Cinnamon 64 bit a few weeks ago and I have been adjusting to Ubuntu 14.04.1 LTS.

I like this distro especially because some of the drivers which failed to load "Lenovo T410S" Keyboard and touchpad did not load properly on LM17.

I recently found out that my HDD is aged and it is about to die so I have ordered a replacement but with SSD, and I wish to return to LM17, I wish to harness all the drivers that are loaded on the Ubuntu, especially because LM17 and Ubuntu 14.04.1 have almost the same repository, I wish to know if it is possible and how I could harness all the drivers currently loaded and install them on LM17 once I get the SSD.

I have read LM17 is based on Ubuntu 14.04 and I must admit that I miss the ability to customizing the desktop environment without breaking the OS. I want LM17 as the OS but I want UBuntu drivers

Thank you for your time
-SJL

---

### Post by tgalati4 on 2014-09-24
To my knowledge, the keyboard and touchpad drivers for a T410S are generic and come with the kernel.  What was the difference in behavior between LM17 and Ubuntu?

You may have to enable multi-touch and swipe actions in preferences and there may be a BIOS setting to turn off the touchpad while typing so the cursor doesn't jump around.

Once you get LM17 loaded, and you have updated (there will be several hundred megabytes of updates) and rebooted, open a terminal:

```
dmesg | more
```

Spacebar to page forward, "q" to quit.  Take note of any keyboard or touchpad errors.

---

### Post by SJLPHI on 2014-09-24
Link is LM forums with my situation regarding it except it was never fully solved.

[http://forums.linuxmint.com/viewtopic.php?f=49&t=173213](http://forums.linuxmint.com/viewtopic.php?f=49&t=173213)

About once every 10 boots, mouse failed to load properly and I had to type
sudo modprobe -r psmouse && sudo modprobe psmouse
to make it work again.

Sonetimes the keyboard didn't load at all, to which I could only reboot.

---

### Post by SJLPHI on 2014-09-24
Adding to that, Ubuntu allows ALL keys to work, the special function buttons as well (Mic on/off for example)

---

### Post by SJLPHI on 2014-09-28
I tried to look into the loaded drivers using lsmod,
How could I match these drivers to repositories?

---

### Post by varunendra on 2014-09-29
If the kernel versions are same, the drivers should be same too. Any difference in performance would then possibly be dependent on further customization through scripts which may further depend on many other packages/settings.

Wouldn't it be easier to simply install the DE that LM17 uses? If this is all due the the 'customization' you like there.

---

### Post by SJLPHI on 2014-09-29
I've somehow managed to break Ubuntu couple of times just from trying to install desktop environment other than Unity on Ubuntu

---

### Post by SJLPHI on 2014-10-01
I am now inclined to disagree to the fact that kernel is solely responsible for the drivers because I have installed the same default kernel 3.13.0.35 and I am still having touchpad/keyboard issues and I took the liberty to upgrade to 3.14.19 which is also bumping into the same problem.

So what controls the driver?

---

### Post by SJLPHI on 2014-10-01
sjl@Concubine2 ~ $ dmesg |grep mouse
[    1.996447] mousedev: PS/2 mouse device common for all mice
[    6.792988] psmouse serio1: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[   61.061661] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd047b3/0xb40000/0xa0000, board id: 71, fw id: 920262
[   61.061674] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[   64.691432] psmouse serio2: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[   66.270374] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3

these are the settings when the mouse is properly loaded

[    3.937505] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3

as to the Keyboard.

Is there a way to force this setting at each boot?

---

### Post by varunendra on 2014-10-01
> **SJLPHI said:**
> So what controls the driver?
The input devices are also controlled by the Xserver settings. The drivers are provided by the kernel, can be controlled by settings applied by external scripts/programs etc. which may differ from one distro to another.

> **SJLPHI said:**
> these are the settings when the mouse is properly loaded

Are the listed settings always different across different sessions? Are the listed settings always the same when it works properly?

I don't know if there is a way to force them. As far as I have seen, only their device no. assignment changes across different sessions, and that is probably the order they are detected by the kernel/Xorg.

---

### Post by SJLPHI on 2014-10-01
Thanks Varun for the reply.
When the touchpad driver is NOT loaded properly, I get "PS/2 Generic mouse"



[COLOR=#333333][FONT=Lucida Grande]sjl@Concubine ~ $ xinput -list[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#9121; Virtual core pointer id=2 [master pointer (3)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#9116; &#8627; Virtual core XTEST pointer id=4 [slave pointer (2)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#9116; &#8627; PS/2 Generic Mouse id=11 [slave pointer (2)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#9123; Virtual core keyboard id=3 [master keyboard (2)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#8627; Virtual core XTEST keyboard id=5 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#8627; Power Button id=6 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#8627; Video Bus id=7 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#8627; Sleep Button id=8 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#8627; Integrated Camera id=9 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#8627; AT Raw Set 2 keyboard id=10 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#8627; ThinkPad Extra Buttons id=12 [slave keyboard (3)]

[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]&#9121; Virtual core pointer id=2 [master pointer (3)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#9116; &#8627; Virtual core XTEST pointer id=4 [slave pointer (2)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#9116; &#8627; SynPS/2 Synaptics TouchPad id=11 [slave pointer (2)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#9116; &#8627; TPPS/2 IBM TrackPoint id=12 [slave pointer (2)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#9123; Virtual core keyboard id=3 [master keyboard (2)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#8627; Virtual core XTEST keyboard id=5 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#8627; Power Button id=6 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#8627; Video Bus id=7 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#8627; Sleep Button id=8 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#8627; Integrated Camera id=9 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#8627; AT Translated Set 2 keyboard id=10 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]&#8627; ThinkPad Extra Buttons

[/FONT][/COLOR]http://forums.linuxmint.com/viewtopic.php?f=49&t=173213

I don't know what is loaded when the keyboard isn't loaded properly simply because I literally cannot do anything

---

### Post by varunendra on 2014-10-02
Have you tried reinstalling your synaptics driver yet? That is -
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install --reinstall xserver-xorg-input-synaptics
```

And is the 'ideapad_laptop' module still blacklisted? I read in the linked thread that you commented it out, just confirming.

---

### Post by SJLPHI on 2014-10-02
I have ran the update and dist-upgrade. 

The thread posted was actually done before I made a short stay at Ubuntu. I have re-blacklisted ideapad_laptop because previously it did seem to make the "misload" less frequent.
I will try the reinstall synaptics now.

---

### Post by SJLPHI on 2014-10-03
unfortunately the re-installation for synaptics didn't help either

---

### Post by SJLPHI on 2014-10-09
I have spoken to a Masters student in Comp-Sci and he mentioned that I will probably need to get package from IBM/Lenovo and modify existing kernel. Any suggestions?

---

### Post by SJLPHI on 2014-10-09
I have spoken to a Masters student in Comp-Sci and he mentioned that I will probably need to get package from IBM/Lenovo and modify existing kernel. Any suggestions?

---

### Post by varunendra on 2014-10-09
> **SJLPHI said:**
> I have spoken to a Masters student in Comp-Sci .... Any suggestions?

Only he/she or an equally qualified person can give any, I'm nowhere close, and I don't want to append a "but.." here. Anything is possible, especially with generic devices like touchpad.

---

### Post by SJLPHI on 2014-10-11
I'm still trying to understand the difference in build between Ubuntu and Linux Mint, I'm not sure what makes Ubuntu to load all of the appropriate drivers from initial install but LM doesn't

---

