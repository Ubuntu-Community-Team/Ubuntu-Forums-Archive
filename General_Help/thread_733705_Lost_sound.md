---
title: "Lost sound"
date: 2008-03-24
forum: General Help
---

### Post by sawdust_prophet on 2008-03-24
My sound worked without a hitch after installing 7.10.  Yesterday, I was working on getting my media keys working properly when somehow my "sleep" button became bound to the "sleep" and "lock screen" functions simulaneously.  After correcting this, I decided to test the sleep button and the screen went black for about 20 seconds, no response.  After that, the computer rebooted, and at that point and since, I have had no speaker sound at all.  My master volume is set to max and all that.

It is also worth noting I am still a bit of a noob to Linux/Ubuntu, but I can find no source for this problem! :(

---

### Post by erginemr on 2008-03-24
There are a few generic commands to identify your sound card and check if it is still recognized by the system. So, can you please post the output of the following commands from a terminal here:
```
aplay -l
```
```
cat /proc/asound/cards
```
```
lspci | grep -i audio
```
```
amixer info
```

---

### Post by sawdust_prophet on 2008-03-24
First code:
> **** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Second code:
>  0 [V8235          ]: VIA8233 - VIA 8235
                      VIA 8235 with VIA1612A at 0xdc00, irq 19


Third code:
> 00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)


Last code:
> Card default 'V8235'/'VIA 8235 with VIA1612A at 0xdc00, irq 19'
  Mixer name    : 'VIA Technologies VIA1612A'
  Components    : 'AC97a:56494161'
  Controls      : 38


Hope it helps, and thanks!

---

### Post by erginemr on 2008-03-24
These results indicate that your sound card is still being recognized by the system, strange... Now I am also clueless. :-k

---

### Post by erginemr on 2008-03-24
Is this an onboard or PCI sound card? (probably the former)

Two similar posts for you to check:
[http://ubuntuforums.org/showthread.php?t=622551](http://ubuntuforums.org/showthread.php?t=622551)
[http://ubuntuforums.org/showthread.php?t=196195](http://ubuntuforums.org/showthread.php?t=196195)

And a third one:
[http://ubuntuforums.org/showthread.php?t=189903](http://ubuntuforums.org/showthread.php?t=189903)

---

### Post by sawdust_prophet on 2008-03-24
Switching jacks didn't work...

A linux-veteran friend of mine (not Ubuntu veteran) suggested my master volume may have been reset to zero.  I have the volume at full via the widget in my upper taskbar, although to get it to change volume properly I had to set it to "headphone."  Maybe that info helps?

---

### Post by erginemr on 2008-03-24
> **sawdust_prophet said:**
> Switching jacks didn't work...

A linux-veteran friend of mine (not Ubuntu veteran) suggested my master volume may have been reset to zero.  I have the volume at full via the widget in my upper taskbar, although to get it to change volume properly I had to set it to "headphone."  Maybe that info helps?

Most probably, the sleep / hibernate has broken or locked some settings in ALSA; the problem is, we don't know which one. Have you given a try to "alsamixer", which by default shows much more volume control widgets than Gnome volume mixer does: Main Menu -> Applications -> Terminal -> alsamixer

Please check and play with all settings there, too. 

Also try the tools "Multimedia Systems Selector" and "Sound", both of which are located under Main Menu -> System -> Preferences, play with the settings and use "Test" button to check if there is any sound. (See the attachments)

If none of these work, I will suggest you to upgrade your ALSA driver to the latest version in an effort to get your sound back, by first enabling **backports** repository downloading an ALSA driver update package, and if the first doesn't work, to recompile ALSA by using two very easy to use scripts by a fellow Ubuntero:
[http://ubuntuforums.org/showpost.php?p=4453784&postcount=8](http://ubuntuforums.org/showpost.php?p=4453784&postcount=8)
[http://ubuntuforums.org/showpost.php?p=4574654&postcount=10](http://ubuntuforums.org/showpost.php?p=4574654&postcount=10)

---

### Post by sawdust_prophet on 2008-03-24
Oh, I think it works now!  I used GNOME ALSA Mixer and changed some settings there...nothing I don't think I already changed...I will do some experimenting to be sure, thanks for the help! :D

---

### Post by erginemr on 2008-03-24
Great! :KS

I am glad that your sound works! I hope it will be persistent...

---

### Post by sawdust_prophet on 2008-03-25
It does seem to be persistent :)  I have even just tested uninstalling the ALSA Mixer and rebooting, and my sound still works :)

But I do have a slightly-related issue now.  Before the crash that caused all this, I had most of my media keys working fine.  Now, my volume and mute keys do not work, and the play/stop/skip keys weren't working in the first place...but they are all recognized in the Keyboard Shortcut settings.  I use Amarok, and have tried both using the Shortcuts settings and Amarok's internal shortcuts...is there something I missed?

---

### Post by erginemr on 2008-03-25
OK. Please do the following experiments:

1. When you run System -> Preferences -> Keyboard Shortcuts and try to change the shortcut of volume mute, what happens? Does the system recognize that you have pressed the media key? Try another key combination such as say, Ctrl+B, and try to use it. Do you see the volume level indicator? Does it have any effect?

2. Open System -> Preferences -> Sound and make sure that "Master" has been selected for keyboard control.

---

### Post by sawdust_prophet on 2008-03-25
Oh wow, that helped a lot!  The sound was indeed set to "Master," I changed it to "headphone" and it works again!  Now to just make Amarok work for me...thank so much!

---

### Post by erginemr on 2008-03-25
Sweeet!.. :guitar:

I don't use amarok, but I am sure you will handle the rest. ;) 

Take care.

---

