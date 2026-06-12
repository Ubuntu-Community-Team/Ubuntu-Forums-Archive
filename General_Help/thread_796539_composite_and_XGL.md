---
title: "composite and XGL"
date: 2008-05-16
forum: General Help
---

### Post by a6s0lu7 on 2008-05-16
Hello, after reading a large number of already created composite threads, im unable to solve my problem so im creating this one.

Ive already got composite to work, BUT, all my graphical performance droped, ive got a ATI 9600 radeon and i figured that the problem was xserver-xgl, cause since i unintstalled it, all got faste prob is without xserver-xgl i cant get composite to work....

So i need some help, ive already tried to edit xorf.conf and put composite to 1 but without luck.

Also, with xgl installed i tried the glxgears and get around some 70 fps removig it, it get around 3000.

Also i have the ati restricted driver on, and from synaptic ive seen that xserver is also installed.

Im really new to ubuntu, so any thing you need to know please post step by step actions or point me to a guide to do that.

Im using 8.04 version.

Thank you.
All help, welcome :)

---

### Post by wootah on 2008-05-22
Bump.

I have exactly the same issue! Without xserver-xgl I get great speeds and hardware acceleration along with dual-head, but as soon as I install xgl, I lose my dual-head along with acceleration and then fglrxinfo says I'm using mesa.

Hmm... does anyone have any light on this?

---

### Post by wootah on 2008-05-22
I found an interesting article that may help. Unfortunately, I am only ssh'd into my machine at home, so I can't test the graphical stuff:

[http://combatwombat.7doves.com/2008/03/10/gutsy_ati_efforts]("http://combatwombat.7doves.com/2008/03/10/gutsy_ati_efforts")

---

### Post by Forlong on 2008-05-22
What version of Ubuntu are you using?

---

### Post by wootah on 2008-05-22
For me, Gutsy 7.10

---

### Post by Forlong on 2008-05-22
Either upgrade to Hardy (Ubuntu 8.04) or install the latest fglrx driver manually.
The version of fglrx included in Ubuntu needs Xgl to run Compiz but the latest one does not.

---

### Post by wootah on 2008-05-22
For my case, I do have the latest fglrx installed (as downloaded from ATI)

---

### Post by Forlong on 2008-05-22
I'm sorry but... what's your problem then?

---

### Post by wootah on 2008-05-22
No composition with or without xserver-xgl.

---

### Post by Forlong on 2008-05-22
Run [this]("http://ubuntuforums.org/showthread.php?t=799070") and post the output here.

---

### Post by wootah on 2008-05-22
Ahh compiz-check. I will do so once I get home in a few hours. Last time I used that tool, I had to modify the code a bit (as I have a dual head setup) because it was bombing on a too many arguments in a test case (author didn't grep for 1 output or manage multi outputs well).

Perhaps he fixed it? Regardless, I'll grab the output and post later.

Thanks!

---

### Post by RAOF on 2008-05-22
My guess will be that the problem is going to be that Composite is explicitly disabled in /etc/X11/xorg.conf.  fglrx users previously needed to do this to get 3D working, but the new drivers handle both Composite and OpenGL at the same time :).

Interesting data here includes: the contents of /var/log/Xorg.0.log and /etc/X11/xorg.conf

---

### Post by wootah on 2008-05-22
```

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

```

#-o! Such an obvious thing! Figures why I didn't notice it! I'll try this suggestion when I get home in a bit. I hope you are right RAOF! :D

---

### Post by wootah on 2008-05-23
Alright some interesting developments:
After leaving my setup as is and turning on composite, it had no effect. So I started playing around with my xorg.conf. I started disabling all suspicious looking things then slowly re-enabling and testing one by one. I found out that what was causing the problem is my dual-head setup!

Is it possible to use compiz with dual heads?

Here is the output I get when attempting to run compiz with the dual head setup:
```

tripp@eclipse-desktop:/usr/bin$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 1002:4152 (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024
640x480) to maximum 3D texture size (2048
2048): [: 352: 2048: unexpected operator
[: 352: 2048: unexpected operator
Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
[B]/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 1
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0[/B]
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```
What's in bold does not appear when I don't enable a dual head setup. Any insights?

EDIT: The other small thing that I found weird was when I did get compiz working, if I ran fglrxinfo while it was running, I would get a pseudolock--nothing on the screen updated graphically, but I could still click things and hoving over buttons (such as the close button) would change the cursor. If I changed to TTY then back to the gui, the screen would be updated. The only way I could fix this was by killing compiz and returning to the gui. Also, my gui is now ALT-CTRL-F9. What happened there?

---

### Post by RAOF on 2008-05-23
Hm.  That looks like you've managed to confuse the compiz script; that would be a bug.  Additionally, I'm not really sure how well fglrx handles multi-head.  Maybe you've hit something that fglrx doesn't handle well?

---

### Post by wootah on 2008-05-23
> **RAOF said:**
> Hm.  That looks like you've managed to confuse the compiz script; that would be a bug.  Additionally, I'm not really sure how well fglrx handles multi-head.  Maybe you've hit something that fglrx doesn't handle well?

Either way, I have had a load less of trouble with nVidia setups :( Do you think I should file a bug report in regards to the compiz script? I have a pretty good idea what is breaking and how to fix it, but the real issue is that compiz.real is failing with the dual head setup.

EDIT: To the op (a6s0lu7), I want to apologize for thread-jacking you here. I hope that any of the information here helps though! :(

---

### Post by a6s0lu7 on 2008-05-25
> **wootah said:**
> 
EDIT: To the op (a6s0lu7), I want to apologize for thread-jacking you here. I hope that any of the information here helps though! :(

Hey, no problem at all, since ur definitely a more advanced user with ubuntu, ive been following up on your discussion with the dev and after posting this:

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

And "turning" it on, it seem its all working now, at least i got composite working, no xserver-xgl, and glxgears now hits +- 2700 fps!! :popcorn:

Anyway, a strange behavior is that scrolling in firefox 3 makes my cpu go 100%.... any idea?

Well, since i cant help with your dual head setup all i can do, is wish good luck to fix that!

So, rock on! :guitar: :lolflag:

---

### Post by RAOF on 2008-05-25
> **wootah said:**
> Either way, I have had a load less of trouble with nVidia setups :( Do you think I should file a bug report in regards to the compiz script? I have a pretty good idea what is breaking and how to fix it, but the real issue is that compiz.real is failing with the dual head setup.
...

It's worth filing the bug against the script.  And then it's worth filing the 'compiz.real doesn't work with my dual head setup' bug, too ;).

---

### Post by wootah on 2008-05-26
> **a6s0lu7 said:**
> Hey, no problem at all, since ur definitely a more advanced user with ubuntu, ive been following up on your discussion with the dev and after posting this:

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

And "turning" it on, it seem its all working now, at least i got composite working, no xserver-xgl, and glxgears now hits +- 2700 fps!! :popcorn:
[B]
Anyway, a strange behavior is that scrolling in firefox 3 makes my cpu go 100%.... any idea?[/B]

Well, since i cant help with your dual head setup all i can do, is wish good luck to fix that!

So, rock on! :guitar: :lolflag:

I hear lots of people have been having difficulties with the beta FF3 in Hardy (I assume you are using Hardy?:)). I'm using Feisty right now--I'm too chicken to do a dist-upgrade cause of the horror stories I have heard :(

Unfortunately I'm not sure how to help with that. I'm glad that the info in this thread did help you out though! Perhaps create another thread with this discussion (FF3 @100% CPU use). There must be others with the same problem :)

---

